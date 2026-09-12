# Project Rules

Tool: tool-neutral (codex, claude, grok, and any CodeNote-routed agent)

## Project Profile

- Name: `orca`
- Path: GitFork clone at `GitFork/orca`
- Origin: `origin=CzzRef/orca`，`upstream=stablyai/orca`
- Local working branch: `czz-dev`（从 fork `main@3b13ce09a51e` / app `1.4.197` 拉出）
- License: MIT, see root `LICENSE`
- Stack: pnpm 12 workspace + TypeScript + Electron (electron-vite) + Vite web client + Expo mobile
- Purpose: 并行 CLI Agent IDE/ADE：本机桌面、配对 Web 客户端、移动 Companion、SSH worktree、`orca serve`
- Initialization date: 2026-09-12

## Detected Manifests

- `package.json` / `pnpm-lock.yaml` / `pnpm-workspace.yaml`
- `electron.vite.config.ts` / `vite.web.config.ts` / `config/electron-builder.config.cjs`
- 官方贡献者入口：根 `AGENTS.md`、`CLAUDE.md`、`.github/CONTRIBUTING.md`
- 产品文档：`docs/site/content/docs/`；贡献约束：`docs/STYLEGUIDE.md`、`docs/reference/`

## Runtime Layout

| Area | Path | Role |
| --- | --- | --- |
| Electron main | `src/main/` | 桌面运行时、配对服务、内嵌 Chromium、打包资源 |
| Renderer | `src/renderer/` | 桌面 UI；配对 Web 客户端从同一 renderer 投影 |
| Web client | `src/renderer/web-index.html`、`src/renderer/src/web/` | 外部浏览器工作台；由运行时托管 `/web-index.html` |
| CLI | `src/cli/`、`config/scripts/orca-dev.mjs` | 已发布 `orca` / 开发 `orca-dev` |
| Relay | `src/relay/`、`cloud/` | 远端配对与云中继，不是本机 AI-DB |
| Mobile | `mobile/` | iOS/Android Companion；独立 Expo 树 |
| Native helpers | `native/` | computer-use / 通知 / CLI launcher |

Directories that do **not** exist and must not be invented: `vibe/ai-db/`, `vibe/requirements/`.

## Local Rule Policy

- Keep project-specific constraints here; move reusable cross-project rules to CodeNote.
- Do not overwrite existing user work or unrelated business files.
- Before implementation, inspect the relevant source paths and the official contributor facts in `local-context.md`.
- Product docs remain in `docs/` and the published site; this file only records agent-facing boundaries.
- `vibe/` belongs to `czz-dev`. Do not include it in PRs to `upstream`.
- UI work follows `docs/STYLEGUIDE.md` and renderer tokens; do not invent a second design system.

## High-Risk Areas

- 配对链接 / pairing token / Tailscale 地址：当作密钥，不要写入任务文档或提交
- Telemetry（PostHog 等）与账号 cookie；不要把 DSN、session cookie、artifact 公链写进仓库
- 代码签名、公证、`ORCA_MAC_RELEASE`、Windows SignPath、自动更新
- Native 模块（`node-pty`、computer-use helpers）与 Linux glibc 2.31 下限
- 可见窗口 / 抢焦点：本机验证必须 `ORCA_BACKGROUND_LAUNCH=1`，不要对用户桌面 `show()` / `app.focus()`
- Computer-use 会操作本机桌面与外部浏览器；未授权不要对真实已登录会话执行
- Relay / cloud Terraform、生产 SQL、推送网关
- 生成物：`out/`、`dist/`、`node_modules/`、`mobile` 构建目录。不要手改

## Business Constraints

- 包管理用仓库锁定的 pnpm；不要发明第二套 npm 脚本入口。
- 源码开发入口是 `pnpm dev` / `orca-dev`；已安装生产包的 `orca` 不是本检出。
- 上游 PR 不要带 `vibe/`。打 GitHub Release、公证、推送 `czz-dev` 必须有当轮明确授权。
- 官方 Cut Release 工作流是维护者路径；不要在普通贡献里改版本号。
