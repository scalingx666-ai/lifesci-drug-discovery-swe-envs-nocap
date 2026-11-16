# Issue

**Title:** feat(sidebar): remove the 400px max width when dragging the file sidebar

## Description

The file-sidebar divider drag clamped the width to 400px (`desktop/App.svelte`), which is too narrow for deep file trees and long filenames. Drop the upper clamp; the 160px minimum, drag-below-80px auto-collapse, and double-click reset to 240px are unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04ffe3b75ca0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.