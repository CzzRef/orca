# CZZ DEMO：主分支迁移与定时 Actions 暂停

Baseline: 2026-09-19；范围：`CzzRef/orca` 默认分支与 inherited `schedule`；状态：implemented-on-demo-branch

## 1. 原实现（基线）

GitHub 默认分支是 `main`。上游 `stablyai/orca` 的 cron 在 fork 的 `main` 上继续跑。
E2E 每天失败两次，Terminal Perf 每天踩预算；上游同期 E2E schedule 也是红的。
Hourly/Daily mac、README badge 已有 `github.repository == 'stablyai/orca'`，在 fork 上 skip。
本地主分支是 `czz-dev`，不是 `main`。

## 2. 相对基线的累计改动

- GitHub 默认主分支改为 `czz-demo`（CZZ DEMO）。本地仍用 `czz-dev`。
- 定时工作流 YAML 留在 `czz-demo`（从 `main` 迁过来），但 `schedule` 一律要求 `vars.CZZ_DEMO_ACTIONS == 'true'`。
- 开关说明：`.github/czz-demo/README.md`。
- 可复用门禁：`.github/workflows/czz-demo-schedule-gate.yml`。

## 3. 影响与风险

- 合进 `czz-demo` 并完成默认分支切换后，fork 不再按 `main` 的 cron 报错。
- 之后若 `git merge upstream/main`，上游可能覆写 job `if`；合并后要再确认门禁仍在。
- 本改动不得送 `upstream`。

## 4. 明确不在范围内

- 不修上游 E2E flake / Terminal Perf 预算。
- 不关 PR 检查、手动 `workflow_dispatch`。
- 不改应用代码。
- 不删除 `main` 分支（仍可用于对照上游）。

## 5. 测试清单

- 正常：默认分支为 `czz-demo`；下一次 cron 为 skipped。
- 空 / 未设变量：`CZZ_DEMO_ACTIONS` 未设时 schedule skip。
- 权限：`workflow_dispatch` 仍可手动跑。
- 并发：不适用。
- 回归：PR Checks 路径未改；`cloud-verify` 的 `push.branches: [main]` 在默认分支切换后不再跟 CZZ DEMO 推送。

## 6. 代码地址

- `.github/workflows/czz-demo-schedule-gate.yml`（整文件）
- `.github/workflows/e2e.yml` `allow_scheduled`（约 L43）
- `.github/workflows/terminal-perf.yml`（约 L56）
- 其余带 `schedule:` 的 workflow：同一 `CZZ_DEMO_ACTIONS` 条件
