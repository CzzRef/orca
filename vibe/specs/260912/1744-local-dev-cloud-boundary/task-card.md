# Task Card

> Standard non-requirement work only.

Tool: grok
Date: 2026-09-12
Task: 1744-local-dev-cloud-boundary

## Task Documentation Sync Group

- Group key: `dsg:orca:1744-local-dev-cloud-boundary`
- Group owner: this `task-card.md`
- Git document prefixes: `vibe/`
- Durable document members: knowledge note, architecture, workflow, project rules, this hub
- Declared code/config dependencies: `electron.vite.config.ts`, `src/main/telemetry/client.ts`, `src/main/orca-profiles/profile-cloud-auth-config.ts`
- Linked current/canonical/rule/memory authorities: [cloud-and-local-pack.md](../../../knowledge/cloud-and-local-pack.md), [architecture.md](../../../knowledge/architecture.md)
- Excluded unrelated dirty documents: CodeNote mixed dirty tree; `node_modules/` / `out/`
- Lookup contract: `get --lookup-only` returns `present/freshness=unchecked`; only `check status=hit` may reuse the gate.

```json documentation-sync-group-v1
{
  "schema": "documentation-sync-group-v1",
  "group_key": "dsg:orca:1744-local-dev-cloud-boundary",
  "group_owner": "vibe/specs/260912/1744-local-dev-cloud-boundary/task-card.md",
  "documents": [
    "vibe/knowledge/cloud-and-local-pack.md",
    "vibe/knowledge/architecture.md",
    "vibe/knowledge/README.md",
    "vibe/rules/workflow.md",
    "vibe/rules/project.md",
    "vibe/specs/PROJECT_STATUS.md",
    "vibe/specs/260912/1744-local-dev-cloud-boundary/task-card.md",
    "vibe/specs/260912/1744-local-dev-cloud-boundary/changes.md",
    "vibe/evals/2026-09-12-local-dev-cloud-boundary.md"
  ],
  "dependencies": [
    "electron.vite.config.ts",
    "src/main/telemetry/client.ts",
    "src/main/orca-profiles/profile-cloud-auth-config.ts"
  ],
  "validators": [],
  "git_scope_prefixes": ["vibe"]
}
```

## Goal And Scope

- Goal: persist the official-vs-local pack / first-party cloud / LAN-only conclusion, record the 2026-09-12 visible `pnpm dev` preview, and commit on local `czz-dev`.
- In scope: project knowledge, architecture, workflow, project rules, hub, this task card; local commit on `czz-dev`.
- Out of scope: application code; pack; `build:web`; login/Relay; push unless this message names it (it does not).
- Success evidence: knowledge note states the three switches; hub points here; `czz-dev` has a local docs commit.

## Decision

- Documentation level: `standard`
- Execution: `main-only`
- Automation lane: `not-applicable`
- Key decision: LAN preview does not need official installer or their cloud; telemetry is official-CI-only; packaged binaries still embed `*.onorca.dev` URLs.
- High-risk / DB boundary: none; no SQL; do not commit pairing URLs or user-data dumps.
- Plan-mode preflight completed before first edit: `yes`
- Plan artifact scope and documentation impact: `project-current`
- Verification map: absent — static analysis plus already-observed `pnpm dev`
- Provisional `VerificationImpactTrace` completed before verification commands: `yes`
- Verification-command provenance: `impact-trace`
- Test additions/execution: impact-selected only; no separate user enumeration required

## Prior Task Overlap

- Relationship: `continuation`
- Prior authority: [1236-ai-rules-init](../1236-ai-rules-init/task-card.md) left `pnpm install` / `pnpm dev` unrun and cloud boundary as follow-up.
- Document governance: architecture Unproven and hub pending-follow-up are replaced by this note.
- Execution logic verification / residual gates: `build:web` / pack / Relay still unrun.
- Traceability and decision: `new-task` for the verified runtime + cloud-boundary docs.

## Documentation Realization

- not applicable (knowledge sync, not a runtime/rule correction)

## Optimization And Template Propagation

- Optimization promotion: `not-applicable`
- Applied project/template impact: this root only
- Parent task / excluded roots: none

## Rule Task Trace

- Registry scope: `project-local / not-admitted`
- Registry identity / row: none
- Requirement and implementation authority: this task card + knowledge note
- Propagation / delegation / Root acceptance: project-local

## Work And Verification

- Changed surface: `vibe/knowledge`, `vibe/rules/{workflow,project}.md`, hub, this task
- Verification: project-mode AI rule audit; authored-file code-link audit
- Unverified gaps: `build:web`, pack, official dmg, packet capture

### Verification Decision

- Route: `static`
- Reason: docs only; runtime evidence already collected in the preview turn
- Impact source and freshness: source + 2026-09-12 `pnpm dev` logs
- Plan verification clauses reconciled before execution: `yes`
- Affected modules / boundaries: cloud URLs, telemetry compile-time gate, local preview
- Checked: knowledge claims against `profile-cloud-auth-config.ts` and `telemetry/client.ts`
- Skipped: re-running `pnpm dev`; pack
- Full-suite escalation: `none`
- Owner: this task card
- Residual risk: Relay retention unproven

### Verification Impact Trace

| Changed surface / claim | Direct consumers | Material transitive or failure boundary | Selected evidence | Skipped suites / reason | Outcome / residual |
| --- | --- | --- | --- | --- | --- |
| Cloud vs telemetry vs LAN | later agents, user pack choice | conflating Relay with PostHog | source + knowledge note | packet capture | documented |
| Visible `pnpm dev` | workflow.md | ORCA_BACKGROUND_LAUNCH hiding the window | Dock `Orca: czz-dev`, CDP 9505 | rebuild | recorded |
| czz-dev commit | user's working branch | vibe/ sent upstream | local commit only | push — not in this message | pending |

## Authority Packet And Documentation Impact

- Authority refs read: orca documentation.md, architecture, workflow, git-batch-commit-push, process/rules §1–3
- Decisive source evidence: `IS_OFFICIAL_BUILD` compile-time; packaged production URLs; 2026-09-12 `pnpm dev`
- `doc_drift`: architecture Unproven still said install/dev unrun
- Document impact: `project-current`
- Synchronized authorities and verification: this repo hubs + knowledge
- Root acceptance gate: local `czz-dev` commit authorized this turn; push not authorized

## Execution Journal

| Event ID | Local Time | Work Unit / Attempt | Actor / Surface | Event | Prior -> Resulting State | Trigger / Evidence | Root Decision / Next Action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| E1 | 2026-09-12 17:43 +08:00 | docs | grok | closeout | Unproven install/dev -> recorded preview + cloud boundary | user: 同步文档并提交 czz-dev | write + commit |

## Efficiency / Token Evidence

| Metric | Baseline | Observed | Delta | Confidence / Source |
| --- | --- | --- | --- | --- |
| runtime usage | n/a | usage unavailable | n/a | host does not expose counters |

## TaskExperienceObservation

- Result: `not applicable`

## Implementation Sync

- Authoritative current behavior: [cloud-and-local-pack.md](../../../knowledge/cloud-and-local-pack.md)
- Module / document mapping: architecture + workflow
- Evidence: 2026-09-12 source and `pnpm dev`

## Closeout

- Sidecar: `main-thread`
- Requirement / business / tech route: knowledge note
- Memory / error route: none
- Evolution Candidate: `none`

## 任务规则声明

- Global entry: CodeNote VibeAi + routing, loaded once
- Project entry: root `AGENTS.md` -> `vibe/rules/README.md`
- Sidecar mode: main-thread
- Document routing: `vibe/rules/documentation.md` + this task card
- High-risk gate: no SQL; no pairing URL in docs; no push
