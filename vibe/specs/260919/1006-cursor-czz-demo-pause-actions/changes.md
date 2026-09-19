# Changes：CZZ DEMO 主分支与 schedule 暂停

## 1. 概览

| 批次 | 说明 |
| --- | --- |
| 门禁 | 所有 inherited `schedule` 要求 `CZZ_DEMO_ACTIONS=true` |
| 默认分支 | GitHub 默认改为 `czz-demo`；本地仍用 `czz-dev` |
| 文档 | vibe 枢纽、error-memory、`.github/czz-demo/README.md` |

## 2. 交付物

| 对象 | 类型 |
| --- | --- |
| `.github/czz-demo/README.md` | 新增：恢复/暂停说明 |
| `.github/workflows/czz-demo-schedule-gate.yml` | 新增：可复用门禁 |
| 带 `schedule:` 的上游 workflow | 改动：同一暂停条件 |
| `vibe/rules/project.md` / `local-context.md` / `PROJECT_STATUS.md` | 改动：主分支约定 |
