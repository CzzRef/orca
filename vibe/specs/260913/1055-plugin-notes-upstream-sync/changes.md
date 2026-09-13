# Changes：Plugin 笔记与追上游

> Inventory only. This file answers which files changed and what each change was.

## 1. 概览

| 批次 | 提交 | 文件数 | 核心说明 |
| --- | --- | --- | --- |
| 合入上游 | `72a09d2999` | 上游 135 提交 + merge | `czz-dev` 合入 `upstream/main` `90b02cba60` |
| 文档同步 | 工作区未提交 | 见下表 | Plugin v0 私有扩展笔记与枢纽 |

## 2. 交付物清单

| 对象 | 类型 | 核心说明 |
| --- | --- | --- |
| `vibe/knowledge/plugins.md` | 新增 | Plugin 装法、能力封闭集、Host API、不能做的事、局域网落点 |
| `vibe/knowledge/architecture.md` | 改动 | 增加 Plugin 模块行；版本基线改为合入后的 upstream |
| `vibe/knowledge/README.md` | 改动 | 索引 plugins.md |
| `vibe/knowledge/cloud-and-local-pack.md` | 改动 | 指向 Plugin 笔记，避免把私有能力默认做成内核包 |
| `vibe/rules/project.md` | 改动 | `czz-dev` 已含当前 upstream/main |
| `vibe/specs/PROJECT_STATUS.md` | 改动 | 当前焦点切到本任务 |
| `vibe/specs/260913/1055-plugin-notes-upstream-sync/task-card.md` | 新增 | 本任务 owner |
| `vibe/specs/260913/1055-plugin-notes-upstream-sync/changes.md` | 新增 | 本清单 |

## 3. 逐批清单

### 合入上游 `72a09d2999`

| 文件 | 核心说明 |
| --- | --- |
| 上游业务树 | ort 无冲突 merge；`vibe/` 未与上游打架 |

### 文档同步 pending

| 文件 | 核心说明 |
| --- | --- |
| `plugins.md` | 私有扩展默认走 Plugin v0 |
| 枢纽 / 架构 / 索引 | 反链与合入后的 SHA |

## 4. 明确没做的（分流，不是遗漏）

| 对象 | 数量 | 核心说明 |
| --- | --- | --- |
| 业务源码（czz 私有） | 0 | 只记 Plugin 面，未改 ADE |
| `origin/main` GitHub Sync | 0 | `gh repo sync` 因缺少 `workflow` scope 失败 |
| `git push` | 0 | 本轮未授权推送；skill 禁止推 origin |
| `pnpm build:mac` / 实装 plugin | 0 | 未授权、未跑 |
| 全量 `git fetch upstream` | 0 | macOS 大小写冲突；只拉了 `upstream/main` |

## 5. 用户可见行为变化

无。应用代码未改。Git 工作区 `czz-dev` 已含上游；官方 Homebrew 1.4.200 不受影响。

## 6. 顺手发现但未处理

| 位置 | 现象 | 核心说明 |
| --- | --- | --- |
| `git fetch upstream`（全量） | 大小写仅差的远程分支无法落盘 | 不要做 `git refs migrate --ref-format=reftable`，除非用户明确授权 |
| `package.json` version | 合入后仍是 `1.4.197` | 上游 main 的 package 版本与 Homebrew 1.4.200 不必相同 |
| `origin/main` | 落后 upstream 11 | 含 workflow 文件，无 `workflow` token 不能 Sync fork |

## 7. 回归数字

- `czz-dev` vs `upstream/main`：ahead 3 / behind 0（2 个既有 vibe 提交 + 1 个 merge）
- `origin/main` vs `upstream/main`：ahead 0 / behind 11
