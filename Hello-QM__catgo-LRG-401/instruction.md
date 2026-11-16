# Issue

**Title:** fix(terminal): left inset so xterm content is not flush against the pane edge

## Description

In side-by-side (structure | terminal) layout the xterm grid sat flush against the terminal pane left edge / the divider — the first column read as clipped. Adds an 8px left padding to `.terminal-container`; FitAddon measures the content box so the grid shifts right without right-side overflow.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca53d1fbef94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.