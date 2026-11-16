# Issue

**Title:** fix(desktop): Split+Overwrite aimed at a terminal leaf escalates instead of no-op

## Description

## Symptom

Full-pane terminal tab (landing page → Terminal) + open mode **Split + Overwrite**: opening a structure file (terminal Ctrl+click, sidebar, or examples) adds it to the tab's structure library but **no structure ever renders**.

## Root cause

The landing "Terminal" button converts the structure tab's only leaf into a terminal leaf — the tab keeps `type: 'structure'`. So the open pipeline finds "a structure tab", and `plan_open(split+overwrite)` returns the **active leaf in place** — which is the terminal leaf. `process_file_content` pushes the library entry (visible in the library column), but `apply_entry_to_pane` has no structure pane to render into. Silent no-op.

(#454 fixed the true `type: 'terminal'` tab case; this is the converted-structure-tab case.)

## Fix

`plan_open`: for `split + overwrite`, check the active leaf. Structure leaf → in-place load, unchanged. Terminal leaf → escalate like `new`: reuse the first empty structure pane, else split beside the terminal, else (pane cap) new tab.

## Verification

- +4 vitest in `tests/desktop/open-target.test.ts` (escalate-to-split, reuse-empty-pane, in-place regression, cap fallback); 25 pass across the three touched suites.
- **Live-verified** on the dev stack at :3100: full-pane terminal + Split/Overwrite + clicking `BaTiO3-tetragonal.poscar` → structure renders in a pane split beside the terminal, terminal preserved.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11545970e5ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.