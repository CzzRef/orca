# GitHub Actions 已停用

`CzzRef/orca` 的工作主分支是 `czz-dev`，不是 `main`，也不是 `czz-demo`。

上游 `stablyai/orca` 的 workflow 已整夹移到这里，GitHub 不会再跑任何自动化。

以后要恢复：把本目录里的 `*.yml` / `*.yaml` 移回 `.github/workflows/`。
不要把本目录推到 `stablyai/orca`。
