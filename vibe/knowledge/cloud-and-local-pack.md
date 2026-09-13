# Official pack, local pack, and first-party cloud

Tool: grok
Date: 2026-09-12
Evidence: official-doc + code + 2026-09-12 local `pnpm install` / `pnpm dev`

## Decision

局域网看效果、不登录、不跨网：源码 `pnpm dev` 即可，不必官方安装包，也不必 `build:mac`。

加私有能力、又不想发 PR：先走实验性 Plugin，不要默认改内核再打包。见 [plugins.md](plugins.md)。

官方 dmg 与本地打包是同一份 MIT 客户端，没有另塞闭源内核。官方**确实运营**可选第一方云；那是登录 / Relay / 分享 / 推送，不是 IDE 本体。

## Three independent switches

| Switch | When it happens | LAN-only, no sign-in |
| --- | --- | --- |
| PostHog telemetry | Official CI pack only (`ORCA_BUILD_IDENTITY` + `ORCA_POSTHOG_WRITE_KEY`). Opt-out in Settings / `DO_NOT_TRACK` / `ORCA_TELEMETRY_DISABLED`. Claims anonymous usage events, not prompts or files. | Local pack and `pnpm dev`: `track()` returns; nothing is sent |
| login / Relay / share / push | You sign in, enable Relay, or publish Artifact/Skill | Not required |
| Local ADE / LAN / Tailscale / this-machine web | Traffic stays on machines you control | This is the default path |

Using their cloud is **not** the same as accepting telemetry. Official installer still has telemetry **even if you never open Relay**, unless you opt out. Local rebuild cannot spoof official telemetry: keys are compile-time, not env vars.

Relay is the path where phone↔desktop frames are spliced through `relay.onorca.dev`. That is not the PostHog pipeline. Source proves transit; it does not prove they persist session bodies.

## First-party endpoints (packaged builds)

Hardcoded when `app.isPackaged` is true (official **and** local `build:mac` / `build:unpack`):

- `https://login.onorca.dev`
- `https://relay.onorca.dev`
- `https://share.onorca.dev`
- `https://push.onorca.dev`

`pnpm dev` is not packaged: cloud sign-in stays unconfigured unless `ORCA_CLOUD_*` is set.

Do not log in, do not open Relay, do not share Artifact/Skill if the goal is to stay off their cloud. Production URLs remain in a packed binary even when unused.

## How we ran it (2026-09-12)

```bash
corepack prepare pnpm@12.0.0 --activate
cd /Users/gdkmjd/work/czz/GitFork/orca
pnpm install
unset ELECTRON_RUN_AS_NODE
unset ORCA_BACKGROUND_LAUNCH   # user asked to see the window
pnpm dev
```

Observed:

- Dock title `Orca: czz-dev`; product `Orca Dev` `1.4.197`
- User data `~/Library/Application Support/orca-dev` (separate from a store install)
- CDP `http://127.0.0.1:9505`
- Web pairing skipped: no `out/web/web-index.html`
- Harmless `GitHub PR lookup failed` in logs

Agent UI checks still use `ORCA_BACKGROUND_LAUNCH=1`. A user-requested visible preview must not set that flag.

## Still unrun

- `pnpm run build:web` and LAN browser pairing
- `pnpm build:mac` / official dmg
- Packet capture proving local-pack zero PostHog egress
- Relay content retention
