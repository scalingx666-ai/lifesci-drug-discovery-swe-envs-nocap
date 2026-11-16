# Issue

**Title:** fix(desktop): Overwrite from a terminal reuses the existing structure pane

## Description

## Symptom

. With Split + **Overwrite** and a terminal focused: the first open correctly splits a structure pane beside the terminal, but every subsequent Ctrl+click splits **another** pane instead of overwriting — Overwrite behaved like New.

## Root cause

Ctrl+clicking a terminal link re-focuses the terminal, so at plan time the active leaf is the terminal again. #455's escalation treated every overwrite-on-terminal like `new` (reuse empty / split), and with no empty pane left it split a fresh one per open.

## Fix

Overwrite aimed at a terminal leaf now targets the tab's **first structure pane** (empty or full) — replace what's showing. Only a tab with no structure pane at all still escalates (split beside the terminal / new tab at cap).

## Verification

- +1 vitest: terminal-active + full structure pane → plan overwrites that pane in place (13 pass in the suite).
- **Live-verified** at :3100: terminal + BaTiO₃ pane → focus terminal → open Fe-BCC.json with Split+Overwrite → Fe replaces BaTiO₃ in the same pane, still two panes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3252bd868c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.