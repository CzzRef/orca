# Changes：orca AI 规则初始化

> Inventory only. This file answers which files changed and what each change was.

## 1. 概览

| 批次 | 提交 | 文件数 | 核心说明 |
| --- | --- | --- | --- |
| 规则初始化 | local-commit | 见下表 | 克隆 fork、建 `czz-dev`、写入 CodeNote 适配层；未改业务代码 |

## 2. 交付物清单

| 对象 | 类型 | 核心说明 |
| --- | --- | --- |
| `/Users/gdkmjd/work/czz/GitFork/orca/` | 新增 clone | `CzzRef/orca` @ `main` `3b13ce09a51e`；本地 `czz-dev` |
| `AGENTS.md` / `CLAUDE.md` | 投影 | 短路由适配器；原贡献者指南进入 `local-context.md` |
| `vibe/rules/` | 新增 | 项目规则、栈/风险、命令、文档路由 |
| `vibe/specs/` | 新增 | 过程枢纽 + 本任务 card/changes |
| `vibe/knowledge/` | 新增 | 架构地图、空 ADR/error-memory 索引 |
| CodeNote `vibe/knowledge/project-index.json` | 改动 | 登记项目身份与 authority routes |
| CodeNote `vibe/knowledge/workspace-config/workspace.local.json` | 改动 | 本机 binding（该文件本就 gitignore） |

## 3. 逐批清单

### 规则初始化 pending

| 文件 | 核心说明 |
| --- | --- |
| Git remotes / `czz-dev` | origin fork + upstream 官方；本地工作分支 |
| `vibe/rules/project.md` | Electron/pnpm/web client 事实与高风险面 |
| `vibe/knowledge/architecture.md` | 从源码核对的模块地图（含外部浏览器工作台） |
| `vibe/specs/260912/1236-ai-rules-init/task-card.md` | Standard 任务卡 |

## 4. 明确没做的（分流，不是遗漏）

| 对象 | 数量 | 核心说明 |
| --- | --- | --- |
| 业务源码 | 0 | 本轮只读理解 |
| `vibe/ai-db/` | 0 | 非 AI-DB 项目 |
| `vibe/requirements/` | 0 | 无需求增量 |
| 远端 `czz-dev` / push | 0 | 未授权 |
| `pnpm install` / `pnpm dev` / 打包 / 配对 | 0 | 未授权 |

## 5. 用户可见行为变化

无。应用代码、CLI、安装包均未改。

## 6. 顺手发现但未处理

| 位置 | 现象 | 核心说明 |
| --- | --- | --- |
| `package.json` homepage | 仍写上游 `stablyai/orca` | fork 元数据，不在本轮改 |
| `pnpm dev` 默认 | 缺少 `out/web` 时跳过配对 Web 构建 | 启用外部浏览器工作台需额外 `build:web` |

## 7. 回归数字

| 批次 | 测试 | 构建 | 静态检查 |
| --- | --- | --- | --- |
| 规则初始化 | 未跑 `pnpm test` | 未构建 | project audit 仅 inherited 短入口；code-link OK |
