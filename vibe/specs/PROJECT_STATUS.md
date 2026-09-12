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

- Status: fork cloned to `GitFork/orca`; local working branch is `czz-dev` from `origin/main` `3b13ce09a51e` (app `1.4.197`). CodeNote AI rule chain initialized. No application code changed.
- Latest task docs: [task card](260912/1236-ai-rules-init/task-card.md), [changes](260912/1236-ai-rules-init/changes.md).
- Remotes: `origin=CzzRef/orca`，`upstream=stablyai/orca`. `czz-dev` is local-only; not pushed.
- CodeNote catalog: `project-index.json` + this-host `workspace.local.json` binding.

## Active Task Index

| Task | Status | Authoritative Doc | Verification | Notes |
| --- | --- | --- | --- | --- |
| AI rules init | `implemented-local / catalog-registered / gitfork-local-committed / unpushed` | [task-card](260912/1236-ai-rules-init/task-card.md) | project audit 仅余官方短入口 inherited | no app code |

## Verification State

- Last verified: 2026-09-12 (docs/rules)
- Commands: CodeNote `audit_ai_rules.py --mode project`；authored-file code-link audit OK；resolver `--project orca`
- Unverified gaps: `pnpm install` / `pnpm dev` / `build:web` / `build:mac`、官方安装包、真实浏览器配对
- Latest Sidecar result: main-thread
- Latest Prior Task Overlap: reference-only GitFork/react-doctor adapter shape; decision `new-task`
- Latest Documentation Impact: `project-current`
- Latest Efficiency / Token Evidence: `usage unavailable`

## Open Risk Or Deploy Gates

- Gate: 官方 Release 签名包 / 本机 `build:mac` / 可见 Electron 窗口 / 对真实网络 `orca serve`
- Blocking condition: this task does not authorize live install, pack, or pairing
- Rollback note: `czz-dev` 仅含上游 `3b13ce09a51e` 加本仓 AI 规则初始化；未推送

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
| 启用外部浏览器工作台 | 本轮说明 | 用户选择官方包或源码 `build:web`/`dev` | 未授权安装/打包 | documented-unrun |

## Memory Routing

- Task rule declaration: recorded on the task card
- Sidecar document route: main-thread
- Prior Task Overlap: GitFork/react-doctor
- Evolution Candidate: none
- Project rules: created this round
- Knowledge: architecture map created this round
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
