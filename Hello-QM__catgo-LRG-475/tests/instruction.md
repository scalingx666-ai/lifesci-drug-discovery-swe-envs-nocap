# Issue

**Title:** fix(terminal): Ctrl+click opens remote files (session_id was dropped)

## Description

## Summary

**Ctrl+clicking a file path in a remote SSH terminal did not open the file**, even when the file exists — the backend returned `"Not found: <path>"` (e.g. `/home/jzhang89/build_prod500.py`, a real 2.8 KB file on Expanse).

## Root cause

An API asymmetry in the terminal click router (`terminal-path-nav.ts`). `open_terminal_click` routes a Ctrl+clicked path to either the Files panel (directory) or the file viewer (file):

- **directory** → `navigate_dir(path, session_id)` ✅ gets `session_id`
- **file** → `open_file(path)` ❌ **`session_id` was dropped**

Downstream, `handle_terminal_leaf_open_file` then fell back to the terminal leaf's own `term.session_id`, which is empty. So `/api/hpc/files/read-content` ran against the **local backend filesystem** instead of the remote SSH session. The directory check (`/api/hpc/files/list`) used the correct session and correctly reported "it's a file"; only the *read* used the wrong (local) session — the backend home differs from the remote home, so an existing remote file came back "Not found".

## Fix

Thread `session_id` through the file-open path, symmetric with `navigate_dir`:

- `open_terminal_click` → `handlers.open_file(path, session_id)`
- `session_id` param added to `TerminalClickHandlers.open_file`, `TerminalPanel.on_open_file`, `TerminalWindow.on_open_file` (optional, backward-compatible)
- `handle_terminal_leaf_open_file` prefers the passed `session_id` over `term.session_id`

Backward compatible: the new parameter is optional; existing callers are unaffected.

## Verification

- **Live-verified on SDSC Expanse**: Ctrl+click now opens remote files in the viewer.
- **Regression test** added to `terminal-path-nav.test.ts` (a remote file's `session_id` is forwarded to `open_file`); the two existing `open_file` assertions were updated for the new signature. **Suite 9/9 pass.**
- **svelte-check**: 0 new errors (the 4 changed files are clean; the pre-existing baseline is untouched).

## Scope

Frontend-only, `+29/−12` across 5 files. Independent of the terminal-disconnect fix in #474.

---
🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eef8a5e1c44f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.