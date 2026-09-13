# Orca Plugin 扩展面（私有能力、不发 PR）

Tool: grok
Date: 2026-09-13
Evidence: official-doc + code（合入 `upstream/main` `90b02cba60` 后的树）

## Decision

要给 Orca 加「别人不一定想要」的能力，**先走官方实验性 Plugin**，不要先改内核、不要先 `pnpm build:mac`。

Plugin 可以装在官方包、`pnpm dev`、本地 ad-hoc 包上，不必推 `stablyai/orca`。内核 fork 只留给 Plugin v0 做不到的事。

产品文档没有独立 Plugin 页；用户面入口是 [Settings → Plugins](../../docs/site/content/docs/settings.mdx)。实现契约在 `src/shared/plugins/` 与 `src/main/plugins/`。

## Status

Host API **v0 / experimental**。`pluginApi` 在清单里是字面量 `1`，但注释写明冻结前无兼容承诺。能力集合是**封闭枚举**：多写一种 `kind` 会校验失败，不会静默授权。

后续阶段才规划带作用域的 kind（如 `net:fetch` 主机、`process:exec` glob）。当前不要假设能发网、能 exec。

## How to load a private plugin

Settings → Plugins：先打开系统，再逐个启用。未同意前不跑。

| 装法 | 位置 | 适合 |
| --- | --- | --- |
| 开发目录 | 全局设置 `devPluginPaths`（目录数组） | 改自己的 plugin；有文件监视刷新 |
| Git marketplace | Settings → Plugins → Marketplaces，加 git 源 | 私有仓库分发；可预览、安装、更新、回滚 |
| 本机已装树 | `<userData>/plugins/<publisher>.<id>/<hash>/` | 安装产物；`current` 指针指向 hash |
| 打进安装包 | `resources/plugins/launch/` | 本地 `build:mac` 时作为 bundled 发布；`examples/` **不会**进包 |

样例：[`examples/plugins/hello-orca/`](../../examples/plugins/hello-orca/)。对抗夹具 `examples/plugins/hostile-panel/` 只给测试用，打包配置明确排除。

官方已 bundled 的内容包在 `resources/plugins/launch/`（导航快捷键、葡萄牙语、Multipass recipes）。私有能力不要改这些文件，另起 `<publisher>.<id>`。

## Manifest (`orca-plugin.json`)

身份是 `<publisher>.<id>`，不是裸 `id`。必填：`manifestVersion: 1`、`id`、`publisher`、`name`、`version`（semver）、`engines.orca`（只接受 `>=x.y.z`）、`pluginApi: 1`。

`contributes`（均可空，有上限）：

| 键 | 上限 | 作用 |
| --- | --- | --- |
| `panels` | 64 | 右侧栏沙箱 HTML 面板 |
| `commands` | 256 | 命令面板项；可声明 `action` 走内置别名、不启动 worker |
| `events` | 3 | 只能订下面三件 |
| `keybindings` | 256 | 绑到本 plugin 的 command |
| `languagePacks` | 16 | i18n 语言包 |
| `vmRecipes` | 64 | Cloud VM / per-workspace 配方 |
| `agents` | 64 | agent profile 文件 |

可订事件（封闭）：`worktree.created`、`worktree.removed`、`agent.status.changed`。

`main` 可选：进程外 **纯 Node worker**（无 Electron）。首次触发才 fork。面板走沙箱 iframe，不能直接碰主进程。

## Capabilities and host methods

清单 `capabilities[]` 与用户同意指纹绑定。运行时每条 host 调用再闸一次。

| kind | 用户同意文案（源码原句） |
| --- | --- |
| `workspace:read` | 读当前聚焦 worktree 的名字、分支、终端列表 |
| `terminal:send` | 向**指定**终端打字（无「当前终端」隐式目标） |
| `notifications:show` | 以 plugin 名显示桌面通知 |
| `storage` | 只写本 plugin 的存储目录 |
| `secrets` | 只读写本 plugin 的加密保险库 |
| `events:subscribe` | worktree 增删、agent 状态变化 |
| `settings:own` | 只读写本 plugin 自己的设置 |

Host API v0 方法（`src/shared/plugins/plugin-host-api.ts`）：

- `workspace.readContext`
- `terminal.sendText`（必须带 `terminalId`）
- `notifications.show`
- `storage.get` / `set` / `delete` / `keys`（单值 ≤256KiB，合计 ≤5MiB，键 ≤1024）
- `secrets.get` / `set` / `delete`
- `settings.get` / `set`
- `events.subscribe`

变更类调用会记审计 `plugin:<id>`。未知 method → `unknown_method`。面板桥不能调用全部方法（例如 storage 对 panel 关闭）。

## What a plugin cannot do

这些需要改内核（`czz-dev` 私有提交），或根本不应做：

- 改主窗口 chrome、编辑器、tab 模型、配对 UI
- 新增 runtime RPC / 终端 opcode / 改 `RUNTIME_PROTOCOL_VERSION`
- 访问 Electron、任意文件系统、任意网络、任意进程
- 替换 Computer Use / native helper
- 改手机 Companion 协议（官方 iOS/Android 对不上）
- 指望「Option+click 换本地包」把未签名 fork 灌进官方 `/Applications/Orca.app`（必须同一 Developer ID 签名）

## LAN / Remote Server

官方说明：plugin worker **永远跑在本机**。对 Remote Orca Server 来说，「本机」是 **Server**，不是 Client 笔记本。

- 私有 plugin 装在 Server 上：官方 Client 连上来时，Server 侧 worker 仍会跑。
- 私有面板 HTML 跟着 Server 的 plugin 树；Client 没有你改过的 renderer 时，看不到内核级 UI。
- 新 RPC 必须按 `docs/reference/remote-wire-compatibility.md` 协商。可选 JSON 字段旧端会忽略；新 opcode 不协商会静默丢帧。私有功能不要 bump 协议号。

局域网远程本身不依赖 Plugin，也不依赖官方安装包。见 [cloud-and-local-pack.md](cloud-and-local-pack.md)。

## Relation to local pack

| 需求 | 路径 |
| --- | --- |
| 自己用、官方包就够 | marketplace 或 `devPluginPaths` |
| 安装包里默认带上 | 把 plugin 放到 `resources/plugins/launch/`，再 `pnpm build:mac` |
| Plugin 做不到 | `czz-dev` 改 `src/`，不要发 upstream PR；`vibe/` 也不要进 upstream |

本地包仍是同一 `appId` `com.stablyai.orca`，会和官方安装抢 userData。开发态 `pnpm dev` 使用单独的 `orca-dev` 数据目录。

## Sample shape

`examples/plugins/hello-orca/orca-plugin.json`：面板 + `hello-ping` 命令 + 订 `worktree.created` / `agent.status.changed`；worker 用 `storage` 计数并用 `notifications.show`。

## Unproven

- 本轮未在 Settings 里实际安装私有 plugin
- 未跑 `pnpm build:mac` 验证 bundled 私有 plugin
- 未用官方 Client 连私有 Server 核对面板/worker 落点
