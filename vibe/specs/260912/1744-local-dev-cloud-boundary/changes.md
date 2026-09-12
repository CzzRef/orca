# Changes：官方包/云边界与源码预览入档

> Inventory only. This file answers which files changed and what each change was.

## 1. 概览

| 批次 | 提交 | 文件数 | 核心说明 |
| --- | --- | --- | --- |
| 文档同步 | local-commit | 见下表 | 把云/遥测/局域网结论和 `pnpm dev` 预览写入 czz-dev |

## 2. 交付物清单

| 对象 | 类型 | 核心说明 |
| --- | --- | --- |
| `vibe/knowledge/cloud-and-local-pack.md` | 新增 | 三开关：遥测、第一方云、局域网 |
| `vibe/knowledge/architecture.md` | 改动 | 补云/遥测模块；Unproven 改为仅余打包与 Web 配对 |
| `vibe/rules/workflow.md` | 改动 | pnpm 12、可见窗口、orca-dev 数据目录 |
| `vibe/rules/project.md` | 改动 | packaged 默认 `*.onorca.dev`；可见窗口授权 |
| `vibe/specs/PROJECT_STATUS.md` | 改动 | 当前焦点切到本任务 |

## 3. 逐批清单

### 文档同步 pending

| 文件 | 核心说明 |
| --- | --- |
| `cloud-and-local-pack.md` | 官方包≠闭源内核；Relay 与 PostHog 分开；本机预览命令 |
| `architecture.md` | 链接知识笔记与 `profile-cloud-auth-config.ts` |
| `workflow.md` / `project.md` | 启动约定与云边界 |

## 4. 明确没做的（分流，不是遗漏）

| 对象 | 数量 | 核心说明 |
| --- | --- | --- |
| 业务源码 | 0 | 只改 vibe |
| `build:web` / 打包 / 推送 | 0 | 未授权 |
| CodeNote catalog | 0 | 用户指定提交 czz-dev（本仓） |

## 5. 用户可见行为变化

无。应用代码未改。`pnpm dev` 若仍在跑，与本轮文档无关。

## 6. 顺手发现但未处理

| 位置 | 现象 | 核心说明 |
| --- | --- | --- |
| 开发日志 | `GitHub PR lookup failed` | 刷新 PR 失败，不影响看界面 |

## 7. 回归数字

| 批次 | 测试 | 构建 | 静态检查 |
| --- | --- | --- | --- |
| 文档同步 | 未重跑 `pnpm test` | 未打包 | project audit inherited；code-link OK |
