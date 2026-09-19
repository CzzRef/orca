# czz-dev：停掉全部 GitHub 自动化

Baseline: 2026-09-19 更正 1006；范围：`CzzRef/orca` Actions；状态：implemented

## 1. 原实现（基线）

1006 误用了 `czz-demo` 名称，且只暂停 `schedule`。用户更正：主分支就是原来的 `czz-dev`，并且要停掉**全部** GitHub 自动化。

## 2. 相对基线的累计改动

- 全部 `.github/workflows/*.{yml,yaml}` 移到 `.github/workflows-paused/`。
- 删除误建的 `czz-demo` 远程分支和 `.github/czz-demo/`、`czz-demo-schedule-gate.yml`。
- 工作主分支保持 `czz-dev`。默认分支若仍是 `main`，`main` 上也做同样搬家，否则 cron 还会读 `main`。

## 3. 影响与风险

- GitHub 不再加载任何 workflow：schedule / push / PR / dispatch 都停。
- 以后恢复：把文件移回 `.github/workflows/`。
- 不要把 `workflows-paused/` 或 `vibe/` 推到 upstream。

## 4. 明确不在范围内

- 不修上游 flake。
- 不改应用代码。
- 不把默认分支改成别的名字。

## 5. 测试清单

- 正常：`.github/workflows/` 无 yml。
- 空：`gh workflow list` 不再出现新的成功/失败 run（旧 run 仍在历史里）。
- 权限：`gh workflow disable` 仍 403，所以用搬家而不是 API。
- 回归：应用代码未改。

## 6. 代码地址

- `.github/workflows-paused/README.md`
- 原 workflow 现位于 `.github/workflows-paused/*.yml`
