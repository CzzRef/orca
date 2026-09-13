# Task Card

> Standard non-requirement work only.

Tool: grok
Date: 2026-09-13
Task: 1055-plugin-notes-upstream-sync

## Task Documentation Sync Group

- Group key: `dsg:orca:1055-plugin-notes-upstream-sync`
- Group owner: this `task-card.md`
- Git document prefixes: `vibe/`
- Durable document members: plugin knowledge, architecture, knowledge index, hub, this card, changes
- Declared code/config dependencies: `src/shared/plugins/`, `examples/plugins/hello-orca/`, `docs/site/content/docs/settings.mdx`
- Linked current/canonical/rule/memory authorities: [plugins.md](../../../knowledge/plugins.md), [cloud-and-local-pack.md](../../../knowledge/cloud-and-local-pack.md)
- Excluded unrelated dirty documents: CodeNote mixed dirty tree; `node_modules/` / `out/`
- Lookup contract: `get --lookup-only` returns `present/freshness=unchecked`; only `check status=hit` may reuse the gate.

```json documentation-sync-group-v1
{
  "schema": "documentation-sync-group-v1",
  "group_key": "dsg:orca:1055-plugin-notes-upstream-sync",
  "group_owner": "vibe/specs/260913/1055-plugin-notes-upstream-sync/task-card.md",
  "documents": [
    "vibe/knowledge/plugins.md",
    "vibe/knowledge/architecture.md",
    "vibe/knowledge/README.md",
    "vibe/knowledge/cloud-and-local-pack.md",
    "vibe/rules/project.md",
    "vibe/specs/PROJECT_STATUS.md",
    "vibe/specs/260913/1055-plugin-notes-upstream-sync/task-card.md",
    "vibe/specs/260913/1055-plugin-notes-upstream-sync/changes.md"
  ],
  "dependencies": [
    "src/shared/plugins/plugin-capabilities.ts",
    "src/shared/plugins/plugin-host-api.ts",
    "src/shared/plugins/plugin-manifest.ts",
    "examples/plugins/hello-orca/orca-plugin.json",
    "docs/site/content/docs/settings.mdx"
  ],
  "validators": [],
  "git_scope_prefixes": ["vibe"]
}
```

## Goal And Scope

- Goal: persist the Plugin v0 private-extension map; merge `upstream/main` into local `czz-dev`.
- In scope: `vibe/knowledge` plugin note and hub links; local merge of `upstream/main`.
- Out of scope: application code; `pnpm build:mac`; push to `origin` unless this message names 推送 (it does not); GitHub Sync of `origin/main` if the token lacks `workflow` scope.
- Success evidence: `plugins.md` exists; `czz-dev` contains `upstream/main`; hub points here.

## Decision

- Documentation level: `standard`
- Execution: `main-only`
- Automation lane: `explicit-cli`（`onboard-czz-fork` 同步上游）
- Key decision: 私有能力默认 Plugin；内核 fork 是后备。同步上游合入 `czz-dev`，不合 `main`、不推 origin。
- High-risk / DB boundary: none; no SQL; no pairing URLs.
- Plan-mode preflight completed before first edit: `yes`
- Plan artifact scope and documentation impact: `project-current`
- Verification map: absent — static analysis of plugin sources + git merge result
- Provisional `VerificationImpactTrace` completed before verification commands: `yes`
- Verification-command provenance: `impact-trace`
- Test additions/execution: impact-selected only; no separate user enumeration required

## Prior Task Overlap

- Relationship: `continuation`
- Prior authority: [1744-local-dev-cloud-boundary](../../260912/1744-local-dev-cloud-boundary/task-card.md) 记录了官方包/云/局域网，未写 Plugin 面，未追上游。
- Document governance: 新增 plugin 知识；不替代 cloud-and-local-pack。
- Execution logic verification / residual gates: Plugin 未实装；`origin/main` 因 workflow scope 未 Sync。
- Traceability and decision: `new-task`

## Documentation Realization

- not applicable (knowledge sync, not a runtime/rule correction)

## Optimization And Template Propagation

- Optimization promotion: `not-applicable`
- Applied project/template impact: `none`
- Parent task / excluded roots: none

## Rule Task Trace

- Registry scope: `project-local / not-admitted`
- Registry identity / row: none
- Requirement and implementation authority: this task card + `plugins.md`
- Propagation / delegation / Root acceptance: none

## Work And Verification

- Changed surface: `vibe/knowledge/plugins.md` and hub links; git merge on `czz-dev`
- Verification: `git merge upstream/main` succeeded; plugin capability/host-api files re-read after merge
- Unverified gaps: private plugin install; GitHub `origin/main` Sync
- Delegated read-only result and Root decision, if any: none

### Verification Decision

- Route: `static`
- Reason: documentation + merge; no UI change
- Impact source and freshness: plugin sources after merge `72a09d2999`
- Plan verification clauses reconciled before execution: `yes`
- Affected modules / boundaries: knowledge + git refs
- Checked: merge working tree; capability enum; host method names; settings.mdx plugin section
- Skipped: `pnpm test`, `build:mac`, live Settings install
- Full-suite escalation: `none`
- Owner: this task card
- Residual risk: `origin/main` still behind; case-insensitive full `git fetch upstream` fails

### Verification Impact Trace

| Changed surface / claim | Direct consumers | Material transitive or failure boundary | Selected evidence | Skipped suites / reason | Outcome / residual |
| --- | --- | --- | --- | --- | --- |
| Plugin v0 能力封闭集 | 私有扩展选型 | 误改内核 / 误 bump 协议 | 源码 `plugin-capabilities.ts` / `plugin-host-api.ts` | 未实装 plugin | 笔记已写 |
| `czz-dev` 含上游 | 后续私有改动基线 | 全量 fetch 大小写冲突 | `git merge upstream/main` → `72a09d2999` | 未 `gh repo sync` | origin/main 落后 11 |

## Authority Packet And Documentation Impact

- Authority refs read: onboard-czz-fork sync-upstream; orca documentation/knowledge rules; plugin shared sources; settings.mdx
- Decisive source evidence: merge commit `72a09d2999`; plugin closed capability set unchanged after merge
- `doc_drift`: `none`
- Document impact: `project-current`
- Synchronized authorities and verification: knowledge + hub
- Root acceptance gate: `accepted`

## Execution Journal

| Event ID | Local Time | Work Unit / Attempt | Actor / Surface | Event | Prior -> Resulting State | Trigger / Evidence | Root Decision / Next Action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| E1 | 2026-09-13 10:55+08 | sync-inspect | git fetch | 全量 `upstream` fetch 因大小写冲突失败 | 未合入 | `sync_upstream.py` exit 2 | 改拉 `upstream/main` |
| E2 | 2026-09-13 11:00+08 | sync-merge | `git merge upstream/main` | ort 无冲突合入 | `2a8f29f0a` → `72a09d2999`（ahead 3 / behind 0） | merge log | 写 plugin 笔记 |
| E3 | 2026-09-13 11:05+08 | remote-sync | `gh repo sync CzzRef/orca` | workflow scope 拒绝 | origin/main 仍 `8641b3af09`，落后 11 | gh stderr | 不推送；报告门禁 |

## Efficiency / Token Evidence

| Metric | Baseline | Observed | Delta | Confidence / Source |
| --- | --- | --- | --- | --- |
| not applicable |  |  |  |  |

## TaskExperienceObservation

- Result: `not applicable`
- Control score / observed dimensions:
- Failed / unavailable dimensions:
- Promotion decision: `not applicable`

## Implementation Sync

- Authoritative current behavior: Plugin v0 as in `plugins.md`; `czz-dev` contains `upstream/main` `90b02cba60`
- Module / document mapping: `vibe/knowledge/plugins.md`
- Evidence: merge commit + source re-read

## Closeout

- Sidecar: `main-thread`
- Requirement / business / tech route: knowledge-only
- Next gate: 用户若要更新 GitHub `CzzRef/orca` 的 `main`，需 `workflow` scope 或明确授权推送；私有能力先按 `plugins.md` 选型
