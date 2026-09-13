# Orca Project Status

Tool: grok
Date: 2026-09-13

## Purpose

Compact process hub for active AI work. This file routes current tasks to project docs without storing durable rules.

## Rule Links

- Project documentation: [../rules/documentation.md](../rules/documentation.md)
- Project knowledge: [../knowledge/README.md](../knowledge/README.md)
- Global process rules: [../../../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/process/rules.md](../../../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/process/rules.md#3-project-location)

## Current Focus

- Status: `czz-dev` 已合入 `upstream/main` `90b02cba60`（merge `72a09d2999`）。Plugin v0 私有扩展笔记已写入。无应用代码改动。
- Latest task docs: [1055 task card](260913/1055-plugin-notes-upstream-sync/task-card.md), [changes](260913/1055-plugin-notes-upstream-sync/changes.md)；权威事实 [plugins.md](../knowledge/plugins.md)。
- Remotes: `origin=CzzRef/orca`，`upstream=stablyai/orca`。`czz-dev` 无 origin 跟踪分支。`origin/main` 落后 upstream 11，GitHub Sync 缺 `workflow` scope。
- CodeNote catalog: 已登记 `orca`；本轮不改 CodeNote。

## Active Task Index

| Task | Status | Authoritative Doc | Verification | Notes |
| --- | --- | --- | --- | --- |
| AI rules init | `implemented-local / catalog-registered / gitfork-local-committed / unpushed` | [task-card](260912/1236-ai-rules-init/task-card.md) | project audit 仅余官方短入口 inherited | no app code |
| Local preview + cloud boundary | `implemented-local / gitfork-local-committed / unpushed` | [task-card](260912/1744-local-dev-cloud-boundary/task-card.md) | `pnpm install`/`pnpm dev` 已观察；code-link OK | 未打包 |
| Plugin notes + 同步上游 | `implemented-local / merge-done / origin-main-blocked` | [task-card](260913/1055-plugin-notes-upstream-sync/task-card.md) | merge 无冲突；plugin 源码复读 | 未推送；未实装 plugin |

## Verification State

- Last verified: 2026-09-13（`git merge upstream/main` + plugin 源码复读）
- Commands: 全量 `git fetch upstream` 失败（大小写）；改拉 `upstream/main` 后 merge 成功
- Unverified gaps: `build:web` / 局域网 Web 配对 / `build:mac` / 官方 dmg / Relay 内容落盘 / 私有 plugin 实装 / `origin/main` Sync
- Latest Sidecar result: main-thread
- Latest Prior Task Overlap: continuation of 1744; decision `new-task`
- Latest Documentation Impact: `project-current`
- Latest Efficiency / Token Evidence: `usage unavailable`

## Open Risk Or Deploy Gates

- Gate: `build:web` / 本机 `build:mac` / 官方签名包 / 对真实网络 `orca serve` / 登录 Relay / GitHub `origin/main` Sync（需 `workflow` scope）
- Blocking condition: 局域网预览已授权；打包与跨网仍未授权；远端 `main` 未更新
- Rollback note: `czz-dev` = 既有 2 个 vibe 提交 + merge `upstream/main`；未推送

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
| GitHub fork `main` | 1055 | 用户授权 `workflow` 或明确推送 | `gh repo sync` / `git push origin` | blocked-workflow-scope |

## Memory Routing

- Task rule declaration: recorded on the task card
- Sidecar document route: main-thread
- Prior Task Overlap: 1744-local-dev-cloud-boundary
- Evolution Candidate: none
- Project rules: created this round
- Knowledge: architecture map + [cloud-and-local-pack.md](../knowledge/cloud-and-local-pack.md) + [plugins.md](../knowledge/plugins.md)
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
