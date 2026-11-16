# Issue

**Title:** fix(desktop): terminal Ctrl+click honors the open target when no structure tab exists

## Description

## Symptom

Active tab is a terminal-only tab (terminal fills the panel), open mode set to **Split + Overwrite**. Ctrl+clicking a structure file in the terminal doesn't open the structure.

## Root cause

`handle_terminal_open_file`'s structure branch only honors the open target when a structure tab already exists. With no structure tab it unconditionally called `parse_and_open_structure_window` — a popout window — ignoring the user's Tab/Split choice. On installed builds where popout windows had no ACL capability (fixed in #453) that window was broken, so the click appeared to do nothing.

## Fix

When no structure tab exists, resolve the open target and route:

- **Window** → popout as before (reuse on overwrite).
- **Tab / Split** → create a fresh structure tab (`open_new_structure_tab`, newly exposed as a sidebar-handler dep) and load into it. A terminal tab has nothing to split, so both collapse to "new tab".
- Tab cap reached (create_tab no-ops) → popout fallback.

Existing structure-tab behavior unchanged.

## Tests

+6 vitest (`tests/vitest/desktop/terminal-open-target.test.ts`): split/tab → new structure tab (popout NOT called), remote origin vs local path plumbing, window target → popout with reuse, tab-cap fallback, existing-structure-tab path unchanged. Full suite: 2049 pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8bce0360638`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.