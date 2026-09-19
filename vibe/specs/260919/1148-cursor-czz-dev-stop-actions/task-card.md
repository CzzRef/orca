# Task Card

> Standard non-requirement work only.

Tool: grok
Date: 2026-09-19
Task: 1148-cursor-czz-dev-stop-actions

## Goal And Scope

- Goal: 主分支用原来的 `czz-dev`（不要 `czz-demo`）；停掉全部 GitHub 自动化。
- In scope: 移走 workflow 文件、删 `czz-demo`、更正枢纽。
- Out of scope: 应用代码；upstream；修 flake。
- Success evidence: `.github/workflows/` 下没有可运行的 yml；`origin/czz-demo` 已删。
