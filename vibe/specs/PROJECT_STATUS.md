# Orca Project Status

Tool: grok
Date: 2026-09-19

## Purpose

Compact process hub for active AI work. This file routes current tasks to project docs without storing durable rules.

## Rule Links

- Project documentation: [../rules/documentation.md](../rules/documentation.md)
- Project knowledge: [../knowledge/README.md](../knowledge/README.md)
- Global process rules: [../../../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/process/rules.md](../../../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/process/rules.md#3-project-location)

## Current Focus

- Status: GitHub 默认主分支改为 `czz-demo`（CZZ DEMO），不再用 `main` 托管定时 Actions。inherited cron 已迁到 demo 分支并暂停（`CZZ_DEMO_ACTIONS`）。
- Latest task docs: [1006 task card](260919/1006-cursor-czz-demo-pause-actions/task-card.md), [260919-cursor-czz-demo-pause-actions.md](260919/1006-cursor-czz-demo-pause-actions/260919-cursor-czz-demo-pause-actions.md)；开关 [czz-demo README](../../.github/czz-demo/README.md)。
- Remotes: `origin=CzzRef/orca`，`upstream=stablyai/orca`。本地工作分支仍是 `czz-dev`。`main` 只作上游对照，不再当默认分支。
- CodeNote catalog: 已登记 `orca`；本轮不改 CodeNote。中央 CodeNote 检出本环境不可用。

## Active Task Index

| Task | Status | Authoritative Doc | Verification | Notes |
| --- | --- | --- | --- | --- |
| AI rules init | `implemented-local / catalog-registered / gitfork-local-committed / unpushed` | [task-card](260912/1236-ai-rules-init/task-card.md) | project audit 仅余官方短入口 inherited | no app code |
| Local preview + cloud boundary | `implemented-local / gitfork-local-committed / unpushed` | [task-card](260912/1744-local-dev-cloud-boundary/task-card.md) | `pnpm install`/`pnpm dev` 已观察；code-link OK | 未打包 |
| Plugin notes + 同步上游 | `implemented-local / merge-done / origin-main-blocked` | [task-card](260913/1055-plugin-notes-upstream-sync/task-card.md) | merge 无冲突；plugin 源码复读 | 未推送；未实装 plugin |
| CZZ DEMO 主分支 + 暂停 schedule | `implemented` | [task-card](260919/1006-cursor-czz-demo-pause-actions/task-card.md) | 默认分支 + `CZZ_DEMO_ACTIONS` 门禁 | 以后设变量即可恢复 |

## Verification State

- Last verified: 2026-09-19（默认分支切换 + schedule 门禁落地）
- Commands: `gh repo view --json defaultBranchRef`；workflow `if` 条件复核
- Unverified gaps: `build:web` / 局域网 Web 配对 / `build:mac` / 官方 dmg / Relay 内容落盘 / 私有 plugin 实装 / 下一次 cron 是否 skipped（需等 UTC 槽）
- Latest Sidecar result: main-thread
- Latest Prior Task Overlap: continuation of 1744; decision `new-task`
- Latest Documentation Impact: `project-current`
- Latest Efficiency / Token Evidence: `usage unavailable`

## Open Risk Or Deploy Gates

- Gate: `build:web` / 本机 `build:mac` / 官方签名包 / 对真实网络 `orca serve` / 登录 Relay / 恢复定时 CI（`CZZ_DEMO_ACTIONS=true`）
- Blocking condition: 局域网预览已授权；打包与跨网仍未授权；定时 Actions 按用户要求暂停
- Rollback note: 把 GitHub 默认分支改回 `main` 会重新托管上游 cron；不要在未开门禁时改回

## Governance Baseline

- Template propagation: accepted global baseline; this project keeps only project-specific routes and does not copy mother-board rules.
- Codex evolution: `v3-route-accepted`; no Hook, supervisor, or rollout change in this repository.
- Rule Task Trace: accepted global baseline; this initialization is project-local and does not add a CodeNote registry row.
- `w24-primary-objective-continuity-accepted`: primary user work remains ahead of advisory governance lanes.
- `w28-documentation-impact-accepted`: this round synchronized project-current adapters/hubs.
- `w30-standard-requirement-owner-accepted`: Standard requirement ownership remains raw requirement plus the Spec owner; this task is Standard non-requirement (task card).

## Pending Follow-ups

| Item | Source turn / task | Owner | Next gate | Status |
| --- | --- | --- | --- | --- |
| 局域网 Web 工作台 | 1744 | 用户若仍要浏览器配对 | `pnpm run build:web` | documented-unrun |
| GitHub fork `main` | 1055 | 已改用 `czz-demo` 作默认主分支 | 不要把 `main` 改回默认 | superseded |
| 恢复 fork 定时 Actions | 1006 | 用户之后要跑 cron 时 | `gh variable set CZZ_DEMO_ACTIONS --body true` | paused |

## Memory Routing

- Task rule declaration: recorded on the task card
- Sidecar document route: main-thread
- Prior Task Overlap: 1744-local-dev-cloud-boundary
- Evolution Candidate: none
- Project rules: created this round
- Knowledge: architecture map + [cloud-and-local-pack.md](../knowledge/cloud-and-local-pack.md) + [plugins.md](../knowledge/plugins.md)
- ADR: empty index only
- Error memory: [260919-cursor-fork-inherited-schedule.md](../knowledge/error-memory/260919-cursor-fork-inherited-schedule.md)
- DB memory: not configured

## Cross-Repository Links

| Concern | Repository | Status Hub |
| --- | --- | --- |
| Rule kernel / catalog | CodeNote | CodeNote `vibe/knowledge/project-index.json` |
| Auto onboard skill | CodeNote | `AiRef/VibePractice/Skills/global/onboard-czz-fork/` |
| ADE 研究条目 | CodeNote | `CzzSolutions/czzGitWorks/EyBell/Inbox/similar-products/ade-research/50-repositories/stablyai--orca/README.md` |

## Next Update Trigger

Update this hub when current focus, active task docs, verification status, open gates, sibling links, or memory routing changes.
