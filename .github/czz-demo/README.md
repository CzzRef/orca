# CZZ DEMO Actions

GitHub 默认主分支是 `czz-demo`（CZZ DEMO），不是上游 `main`。
本地工作分支仍是 `czz-dev`，与 `czz-demo` 同内容。

## 定时自动化（已暂停）

从 `main` 继承的 `schedule` 工作流已迁到本分支，但默认不跑。

恢复（之后要用时）：

```bash
gh variable set CZZ_DEMO_ACTIONS --body true --repo CzzRef/orca
```

再次暂停：

```bash
gh variable set CZZ_DEMO_ACTIONS --body false --repo CzzRef/orca
```

未设置或不是 `true` 时，所有 `schedule` 触发都会 skip。
`workflow_dispatch`、`workflow_call`、PR 检查不受这个开关影响。

## 不要做的事

- 不要把 `main` 改回默认分支，除非准备重新托管上游 cron。
- 不要把本目录或 `vibe/` 推到 `stablyai/orca`。
