# Task Card

> Standard non-requirement work only.

Tool: grok
Date: 2026-09-12
Task: 1236-ai-rules-init

## Task Documentation Sync Group

- Group key: `dsg:orca:1236-ai-rules-init`
- Group owner: this `task-card.md`
- Git document prefixes: `AGENTS.md`, `CLAUDE.md`, `vibe/`
- Durable document members: adapters, `vibe/rules/*`, `vibe/specs/*`, `vibe/knowledge/*`; CodeNote `vibe/knowledge/project-index.json` and ignored `workspace.local.json`
- Declared code/config dependencies: none (read-only on application source)
- Linked current/canonical/rule/memory authorities: CodeNote starter-kit, configure-agent-ecosystem project-rules, GitFork/react-doctor adapter shape, this hub
- Excluded unrelated dirty documents: CodeNote mixed dirty tree except the catalog row, hub row and onboard skill for this project
- Lookup contract: `get --lookup-only` returns `present/freshness=unchecked`; only `check status=hit` may reuse the gate.

```json documentation-sync-group-v1
{
  "schema": "documentation-sync-group-v1",
  "group_key": "dsg:orca:1236-ai-rules-init",
  "group_owner": "vibe/specs/260912/1236-ai-rules-init/task-card.md",
  "documents": [
    "AGENTS.md",
    "CLAUDE.md",
    "vibe/rules/README.md",
    "vibe/rules/local-context.md",
    "vibe/rules/project.md",
    "vibe/rules/workflow.md",
    "vibe/rules/knowledge.md",
    "vibe/rules/documentation.md",
    "vibe/specs/README.md",
    "vibe/specs/PROJECT_STATUS.md",
    "vibe/specs/260912/1236-ai-rules-init/task-card.md",
    "vibe/specs/260912/1236-ai-rules-init/changes.md",
    "vibe/knowledge/README.md",
    "vibe/knowledge/architecture.md",
    "vibe/knowledge/adr/README.md",
    "vibe/knowledge/error-memory/README.md"
  ],
  "dependencies": ["package.json", "pnpm-workspace.yaml", "AGENTS.md", "src/renderer/web-index.html"],
  "validators": [],
  "git_scope_prefixes": ["AGENTS.md", "CLAUDE.md", "vibe"]
}
```

## Goal And Scope

- Goal: place the CzzRef fork at the GitFork checkout, make `czz-dev` the local working branch, initialize the CodeNote adapter/rule/knowledge/process chain, and explain how to enable the external-browser workbench.
- In scope: clone; `origin`/`upstream`; local `czz-dev`; short adapters; `vibe/rules`; `vibe/knowledge`; `vibe/specs`; CodeNote catalog + this-host binding; project-rules publication; local commit after init; install-vs-local-pack explanation.
- Out of scope: application code; `pnpm install` / live Electron / pack / pairing; push; sending `vibe/` upstream; Home/Hook/MCP machine apply.
- Success evidence: checkout exists on `czz-dev`; project audit green or only inherited official-entry findings; adapters route to CodeNote master or portable projections; resolver `--project orca` matches this clone.

## Decision

- Documentation level: `standard`
- Execution: `main-only`
- Automation lane: `not-applicable`
- Key decision and reason: apply the current starter-kit + project-rules publisher used by GitFork/react-doctor; do not copy VibeAi body; do not enable intent-note, design-preference, or AI-DB; keep official contributor facts in `local-context.md`.
- High-risk / DB boundary: none; no SQL; no live install, pack, or pairing.
- Plan-mode preflight completed before first edit: `yes`
- Plan artifact scope and documentation impact: `project-current`
- Verification map: absent — static analysis
- Provisional `VerificationImpactTrace` completed before verification commands: `yes`
- Verification-command provenance: `impact-trace`
- Test additions/execution: impact-selected only; no separate user enumeration required

## Prior Task Overlap

- Relationship: `reference-only`
- Prior authority and verified state: GitFork/react-doctor `260908/1302-ai-rules-init` already encodes the downstream adapter shape.
- Document governance: this repository had official `AGENTS.md` / `CLAUDE.md` but no `vibe/` tree before this task.
- Execution logic verification / residual gates: CodeNote catalog had no `orca` row before this turn.
- Traceability and decision: `new-task` with template delta (do not rerun those migrations).

## Documentation Realization

- not applicable (initialization, not a runtime/rule correction)

## Optimization And Template Propagation

- Optimization promotion: `not-applicable`
- Applied project/template impact: this root only; starter-kit unchanged
- Parent task / excluded roots: CodeNote `onboard-czz-fork` skill records the reusable workflow

## Rule Task Trace

- Registry scope: `project-local / not-admitted`
- Registry identity / row: none
- Requirement and implementation authority: this task card + project rules
- Propagation / delegation / Root acceptance: project-local

## Work And Verification

- Changed surface: clone + czz-dev; adapters; new vibe tree; CodeNote project-index + workspace binding
- Verification: project-mode AI rule audit; authored-file code-link audit; resolver `--project orca`
- Unverified gaps: `pnpm install` / `pnpm dev` / `build:web` / pack / push

### Verification Decision

- Route: `static`
- Reason: docs/rules only; no executable behavior change
- Impact source and freshness: inspected 2026-09-12 source tree at `3b13ce09a51e`
- Plan verification clauses reconciled before execution: `yes`
- Affected modules / boundaries: adapters, vibe tree, CodeNote catalog
- Checked: clone remotes and `czz-dev` at `3b13ce09a51e`
- Skipped: app tests; live install; pack; pairing
- Full-suite escalation: `none`
- Owner: this task card
- Residual risk: application runtime unproven

### Verification Impact Trace

| Changed surface / claim | Direct consumers | Material transitive or failure boundary | Selected evidence | Skipped suites / reason | Outcome / residual |
| --- | --- | --- | --- | --- | --- |
| GitFork clone + `czz-dev` | later implementation tasks | wrong remote or branch | `git remote -v`; `czz-dev` == `3b13ce09a51e` | push — not authorized | pending closeout |
| New short adapters / `vibe/rules` | future agents in this repo | broken relative link to CodeNote master | `audit_ai_rules.py --mode project` | app tests — no behavior change | pending |
| CodeNote `project-index.json` | workspace resolver | invalid identity/markers | resolver `--project orca` | full master audit — catalog row only | pending |
| Application source | runtime | none this round | read-only | live install/pack | no code change |

## Authority Packet And Documentation Impact

- Authority refs read: session-title, routing, VibeAi, CodeNote project entry, starter-kit, configure-agent-ecosystem project-rules, GitFork/react-doctor adapters, process/rules §1–3, onboard-czz-fork
- Decisive source evidence: this checkout had official adapters and no `vibe/` tree; GitFork is the established fork root; `CzzRef/orca` is a controllable fork of `stablyai/orca`
- `doc_drift`: none in this repository
- Document impact: `project-current`
- Synchronized authorities and verification: this repo hubs + CodeNote catalog
- Root acceptance gate: `accepted` for this repository; local commit authorized this turn via onboard skill; push not authorized

## Execution Journal

| Event ID | Local Time | Work Unit / Attempt | Actor / Surface | Event | Prior -> Resulting State | Trigger / Evidence | Root Decision / Next Action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| E1 | 2026-09-12 12:20 +08:00 | inspect | grok | detect | no local clone -> confirmed controllable | `CzzRef/orca` fork of `stablyai/orca` | clone to GitFork |
| E2 | 2026-09-12 12:24 +08:00 | git | grok | clone + czz-dev | empty path -> `3b13ce09a51e` on `czz-dev` | origin CzzRef, upstream stablyai | write vibe tree |
| E3 | 2026-09-12 12:36 +08:00 | adapters | grok | write vibe owners | uninitialized -> CodeNote chain | starter-kit / project-rules compiler | publish + verify |
| E4 | 2026-09-12 12:40 +08:00 | verify | grok | project-rules apply + audit | unpublished -> inherited short-entry findings only | apply 4 files; resolver `--project orca` | local-commit |

## Efficiency / Token Evidence

| Metric | Baseline | Observed | Delta | Confidence / Source |
| --- | --- | --- | --- | --- |
| runtime usage | n/a | usage unavailable | n/a | host does not expose counters |

## TaskExperienceObservation

- Result: `not applicable`

## Implementation Sync

- Authoritative current behavior: [architecture.md](../../../knowledge/architecture.md)
- Module / document mapping: product docs remain in `docs/site/content/docs/`; agent facts in [project.md](../../../rules/project.md)
- Evidence: source read 2026-09-12; runtime unproven

## Closeout

- Sidecar: `main-thread`
- Requirement / business / tech route: no product requirement delta; architecture map written
- Memory / error route: project knowledge created; error archive none
- Evolution Candidate: `none`

## 任务规则声明

- Global entry: CodeNote VibeAi + routing, loaded once
- Project entry: root `AGENTS.md` -> `vibe/rules/README.md`
- Sidecar mode: main-thread
- Document routing: `vibe/rules/documentation.md` + this task card
- High-risk gate: no SQL mutation; no live install / pack / pairing; no overwrite of unrelated dirty files
