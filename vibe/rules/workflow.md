# Workflow Rules

Tool: tool-neutral (codex, claude, grok, and any CodeNote-routed agent)

## Commands

Prefer documented project scripts over inventing new ones. Do not run a visible Electron window、computer-use、签名发布或 `orca serve` 对真实网络暴露，unless the current task explicitly authorizes them.

```bash
pnpm install                 # 安装依赖；postinstall 会 rebuild native
pnpm dev                     # Electron 开发；默认不构建配对 Web 客户端
pnpm tc                      # typecheck（node / cli / web）
pnpm test [path]             # vitest
pnpm run check:code-quality:changed
pnpm run build:web           # 配对用外部浏览器工作台
pnpm run build:mac           # 本机未签名 macOS 包（ suffixed local version ）
pnpm run build:unpack        # 未打包目录，便于检查产物
```

开发本仓时不要用已安装的生产 `orca` 代替 `pnpm exec orca-dev`。`pnpm dev` 若缺少 `out/web/web-index.html`，会跳过配对 Web 构建；需要浏览器配对时先 `pnpm run build:web` 或设 `ORCA_DEV_WEB_PREPARE=1`。

源码路径要求 pnpm `12`（见根 `package.json` `packageManager`）和 Electron 运行时（`pnpm run ensure:electron-runtime`）。

## Verification

- Rule-only edits: run the CodeNote project audit below. Do not `pnpm install`、启动桌面窗口或打包只为证明文档。
- Code changes: run the nearest focused `pnpm test` path and `pnpm tc` for the affected surface (`tc:node` / `tc:cli` / `tc:web`).
- UI checks: follow official `AGENTS.md` — background launch + Playwright CDP; do not use computer-use to validate Orca UI.
- Do not claim desktop smoke、e2e、签名安装包或浏览器配对已通过 without runtime evidence.
- For documentation-heavy changes, validate Markdown links and record unresolved links.

## Required AI Rule Audit

From the repository root, using the CodeNote audit relative to this clone:

```bash
python3 ../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/scripts/audit_ai_rules.py . --mode project --fix-links
python3 ../../CzzProj/CodeNote/AiRef/VibePractice/Vibe_Rules/scripts/audit_ai_rules.py . --mode project
```
