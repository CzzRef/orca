# Orca Project Status

Tool: grok
Date: 2026-09-12

## Purpose

Compact process hub for active AI work. This file routes current tasks to project docs without storing durable rules.

## Rule Links

- Project documentation: [../rules/documentation.md](../rules/documentation.md)
- Project knowledge: [../knowledge/README.md](../knowledge/README.md)
- Global process rules: [../../../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/process/rules.md](../../../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/process/rules.md#3-project-location)

## Current Focus

- Status: `czz-dev` 已落地规则链，并完成本机可见 `pnpm dev`。官方包与第一方云边界已写入知识笔记。无应用代码改动。
- Latest task docs: [1744 task card](260912/1744-local-dev-cloud-boundary/task-card.md), [changes](260912/1744-local-dev-cloud-boundary/changes.md)；权威事实 [cloud-and-local-pack.md](../knowledge/cloud-and-local-pack.md).
- Remotes: `origin=CzzRef/orca`，`upstream=stablyai/orca`. `czz-dev` 仍无 upstream。
- CodeNote catalog: 已登记 `orca`；本轮不改 CodeNote。

## Active Task Index

| Task | Status | Authoritative Doc | Verification | Notes |
| --- | --- | --- | --- | --- |
| AI rules init | `implemented-local / catalog-registered / gitfork-local-committed / unpushed` | [task-card](260912/1236-ai-rules-init/task-card.md) | project audit 仅余官方短入口 inherited | no app code |
| Local preview + cloud boundary | `implemented-local / gitfork-local-committed / unpushed` | [task-card](260912/1744-local-dev-cloud-boundary/task-card.md) | `pnpm install`/`pnpm dev` 已观察；code-link OK | 未打包 |

## Verification State

- Last verified: 2026-09-12 (`pnpm install` + visible `pnpm dev`)
- Commands: project audit 仅 inherited 短入口；code-link OK
- Unverified gaps: `build:web` / 局域网 Web 配对 / `build:mac` / 官方 dmg / Relay 内容落盘
- Latest Sidecar result: main-thread
- Latest Prior Task Overlap: reference-only GitFork/react-doctor adapter shape; decision `new-task`
- Latest Documentation Impact: `project-current`
- Latest Efficiency / Token Evidence: `usage unavailable`

## Open Risk Or Deploy Gates

- Gate: `build:web` / 本机 `build:mac` / 官方签名包 / 对真实网络 `orca serve` / 登录 Relay
- Blocking condition: 局域网预览已授权；打包与跨网仍未授权
- Rollback note: `czz-dev` 相对 `origin/main` `3b13ce09a51e` 仅 vibe/适配器；未推送

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

## Memory Routing

- Task rule declaration: recorded on the task card
- Sidecar document route: main-thread
- Prior Task Overlap: GitFork/react-doctor
- Evolution Candidate: none
- Project rules: created this round
- Knowledge: architecture map + [cloud-and-local-pack.md](../knowledge/cloud-and-local-pack.md)
- ADR: empty index only
- Error memory: empty index
- DB memory: not configured

## Cross-Repository Links

| Concern | Repository | Status Hub |
| --- | --- | --- |
| Rule kernel / catalog | CodeNote | CodeNote `vibe/knowledge/project-index.json` |
| Auto onboard skill | CodeNote | `AiRef/VibePractice/Skills/global/onboard-czz-fork/` |
| ADE 研究条目 | CodeNote | `CzzSolutions/czzGitWorks/EyBell/Inbox/similar-products/ade-research/50-repositories/stablyai--orca/README.md` |

## Next Update Trigger

Update this hub when current focus, active task docs, verification status, open gates, sibling links, or memory routing changes.
