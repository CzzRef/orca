# Task Card

> Standard non-requirement work only.

Tool: grok
Date: 2026-09-19
Task: 1006-cursor-czz-demo-pause-actions

## Goal And Scope

- Goal: 把 fork 的 GitHub 主分支从 `main` 换成 CZZ DEMO（`czz-demo`），把 `main` 上的定时自动化迁过去并全部暂停，以后用 `CZZ_DEMO_ACTIONS` 再开。
- In scope: 默认分支、schedule 门禁、`.github/czz-demo/`、过程枢纽。
- Out of scope: 上游 flake 修复；应用代码；推 `upstream`。
- Success evidence: `default_branch=czz-demo`；下一次 cron 为 skipped。

## Decision

- Documentation level: `standard`
- Key decision: 本地仍用 `czz-dev`；GitHub 默认用 `czz-demo`。cron YAML 保留在 demo 分支，靠变量暂停。
- High-risk / DB boundary: none

## Test Checklist

- 正常：默认分支切换成功；schedule skip
- 空变量：未设 `CZZ_DEMO_ACTIONS` 时 skip
- 权限：手动 dispatch 仍可用
- 回归：PR Checks 不因门禁被关
