# Orca Architecture Map

Tool: grok
Date: 2026-09-12

## Sync Rule

Update this file when a maintained module's entrypoint, storage/data contract, integration boundary, key workflow, or verification command changes. Keep entries as module + technology + code address. Do not copy the official contributor guide.

## Request Path

```text
Desktop Electron / paired web client / mobile / CLI
  └─ runtime (src/main) owns worktrees, terminals, agents, pairing
      ├─ renderer UI (src/renderer)
      ├─ web client (src/renderer/src/web + out/web/web-index.html)
      ├─ per-worktree Chromium browser (embedded, not the web client)
      ├─ CLI (src/cli / orca-dev)
      └─ optional orca serve (headless pairing host)
```

Two different “browsers”:

1. **Embedded worktree browser** — Chromium pane inside the desktop app.
2. **External browser workbench** — paired web client opened in Chrome/Safari at `/web-index.html`. It is a UI client of a running Orca runtime, not a standalone hosted product.

## Module Index

| Module | Technology / Mechanism | Code Address | Current Notes | Last Verified |
| --- | --- | --- | --- | --- |
| App version | package | [../../package.json](../../package.json#L3) | `1.4.197` at clone `3b13ce09a51e` | 2026-09-12 |
| Electron main | electron-vite | [../../electron.vite.config.ts](../../electron.vite.config.ts#L217) | `src/main/index.ts` | 2026-09-12 |
| Web client page | HTML | [../../src/renderer/web-index.html](../../src/renderer/web-index.html#L1) | title `Orca Web` | 2026-09-12 |
| Web client boot | React | [../../src/renderer/src/web/main.tsx](../../src/renderer/src/web/main.tsx#L1) | pairing hash → stored runtime | 2026-09-12 |
| Dev web prepare | Node script | [../../config/scripts/run-electron-vite-dev.mjs](../../config/scripts/run-electron-vite-dev.mjs#L534) | 缺 bundle 时跳过；`build:web` 或 `ORCA_DEV_WEB_PREPARE=1` | 2026-09-12 |
| Local setup | contributor guide | [../../.github/CONTRIBUTING.md](../../.github/CONTRIBUTING.md#L17) | `pnpm install` + `pnpm dev` | 2026-09-12 |
| Install path | product docs | [../../docs/site/content/docs/install.mdx](../../docs/site/content/docs/install.mdx#L1) | 官方 dmg/exe/AppImage / Homebrew | 2026-09-12 |
| Ways to run | product docs | [../../docs/site/content/docs/ways-to-run.mdx](../../docs/site/content/docs/ways-to-run.mdx#L1) | local / SSH / remote server / Cloud VM | 2026-09-12 |
| Remote server | product docs | [../../docs/site/content/docs/remote-servers.mdx](../../docs/site/content/docs/remote-servers.mdx#L1) | 桌面分享或 `orca serve` | 2026-09-12 |
| Embedded browser | product docs | [../../docs/site/content/docs/browser/overview.mdx](../../docs/site/content/docs/browser/overview.mdx#L1) | per-worktree Chromium | 2026-09-12 |
| Local mac pack | script | [../../config/scripts/build-mac-local.mjs](../../config/scripts/build-mac-local.mjs#L1) | `pnpm build:mac` 写 `local.<ts>.<commit>` 版本 | 2026-09-12 |

## Data Contract

- 配对 URL 含 token，等同密钥。
- Web 客户端由 **正在运行的 Orca runtime** 托管静态页；没有独立的官方“只开浏览器、不跑 runtime”产品。
- 官方安装包已含 web 产物。源码 `pnpm dev` 默认不含；本地 `build:desktop` / `build:mac` / `build:web` 可生成。
- Telemetry 与账号状态不要写入任务文档。
- 生成物 `out/`、`dist/`、`node_modules/` 不手改。

## Unproven

- `pnpm install` / `pnpm dev` / `pnpm build:web` / `pnpm build:mac`、官方 dmg 安装、真实浏览器配对均未在 2026-09-12 规则初始化任务中执行。
