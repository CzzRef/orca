# Fork 继承上游 schedule 会在 main 上报红

- Symptom: `CzzRef/orca` 的 Actions 持续失败（E2E 每天两次、Terminal Perf 每天一次）。
- Wrong assumption: 这是本 fork 业务代码坏了，或只关某一个 workflow 即可。
- Root cause: GitHub 只在**默认分支**上跑 `schedule`。fork 默认曾是 `main`，完整继承了 `stablyai/orca` 的 cron。失败内容与上游同期 E2E schedule 同类 flake；fork 没有那些预算和归属。
- Evidence: `gh run list --status failure`；上游 `stablyai/orca` E2E schedule 同样 failure；`gh workflow disable` 因 token 无 Actions 写权限 403。
- Prevention: 默认分支用 `czz-demo`（CZZ DEMO）。`schedule` 必须 `vars.CZZ_DEMO_ACTIONS == 'true'` 才跑。恢复方式见 `.github/czz-demo/README.md`。
- Paths: `.github/workflows/czz-demo-schedule-gate.yml`；`.github/workflows/e2e.yml`；`.github/workflows/terminal-perf.yml`
