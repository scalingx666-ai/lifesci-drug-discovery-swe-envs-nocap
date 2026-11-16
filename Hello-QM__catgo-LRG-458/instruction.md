# Issue

**Title:** fix(desktop): popout structure load survives a restored terminal tab

## Description

## Symptom

**Window + Overwrite** (and Window + New): the popout opens but shows a clone of the main window's terminal tab instead of the structure — "nothing opens". State-dependent: it only reproduces once the persisted active tab is a terminal, which is why it looked like #457 caused it.

## Root cause

`load_popout_structure` wrote into the **active leaf's** structure pane and silently returned if there wasn't one. Popout windows share localStorage with the main window, so the popout restores the main window's persisted tab set — a restored full-pane terminal tab has no structure pane on its active leaf, and the payload was dropped on the floor.

## Fix

Fallback chain, payload never dropped:
1. active leaf's structure pane (unchanged fast path)
2. the tab's first structure pane
3. `pending_open_structure` signal — the app's existing "open in a new structure tab" effect creates a proper tab

## Verification

- +4 vitest (`tests/vitest/desktop/popout-load.test.ts`): active-structure-leaf, terminal-active-with-sibling-pane, terminal-only → pending, no-ts → pending.
- **Live-verified** at :3100 with a persisted terminal tab: Window+Overwrite popout now renders BaTiO₃.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4219781c0403`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.