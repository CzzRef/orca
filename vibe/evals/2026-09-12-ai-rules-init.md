# AI Rules Initialization Eval

Tool: grok
Project: `orca`
Date: 2026-09-12

## Migration Summary

- Cloned `git@github.com:CzzRef/orca.git` to `GitFork/orca`.
- Added `upstream=stablyai/orca` and created local working branch `czz-dev` at `3b13ce09a51e` (app `1.4.197`).
- Applied CodeNote project-rules projections: `AGENTS.md`, `CLAUDE.md`, `vibe/rules/`.
- Official contributor `AGENTS.md` was extracted into `vibe/rules/local-context.md`.
- Did not copy the CodeNote master body.
- DB workspace created: no.
- Requirement Manifest created: no.

## Verification

### Detector

`onboard-czz-fork` `detect_czz_fork.py --probe` on the original SSH URL: `is_known_fork_owner=true`, `fork=true`, `parent=stablyai/orca`.

### Final Project Audit

```text
AI rule audit [working]: ISSUES
- adapter does not route to documentation rules: AGENTS.md
- adapter does not route to process hub: AGENTS.md
- adapter does not route to project rules: CLAUDE.md
- adapter does not route to documentation rules: CLAUDE.md
- adapter does not route to process hub: CLAUDE.md
```

These match the current official short-entry projection on GitFork/react-doctor. They are inherited publisher shape, not this clone's extra drift.

### Authored Code Link Audit

`audit_code_links.py --root GitFork/orca` on `vibe/` + adapters: `OK`.

### Workspace Resolver

```text
--project orca -> /Users/gdkmjd/work/czz/GitFork/orca
routes: entry=AGENTS.md, rules=vibe/rules/README.md, status=vibe/specs/PROJECT_STATUS.md
```

## Remaining Notes

- Default project audit checks AI rule surfaces only.
- `pnpm install` / `pnpm dev` / `build:web` / official installer / live pairing not executed.
- `czz-dev` is local-only until the authorized init commit.
