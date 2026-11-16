# Issue

**Title:** fix(desktop): Window+Overwrite reuse popout now reloads its structure

## Description

## Symptom

Open mode **Window + Overwrite**: the first file opens a popout, but every later open only focuses that popout — it keeps showing the first structure. Only one structure can ever be opened.

## Root cause

The reuse path (`open_structure_in_new_window`, `reuse=true`) writes a fresh localStorage payload and emits `catgo-reload-structure` at the existing `structure-reuse` window. **No listener for that event exists anywhere in the codebase** — the emit has been dead code since the reuse feature landed. (The browser fallback works because `window.open` with a fixed name re-navigates the named window.)

## Fix

The popout's `#structure` hash route now registers a Tauri event listener: on `catgo-reload-structure`, re-run `load_popout_structure` with the pushed key. Listener lifetime = popout window lifetime. Depends on #453 (structure-* windows now have event permissions).

## Verification

- Existing open-target suites pass (19).
- Tauri event plumbing isn't reachable from jsdom/browser; needs a native check: Window+Overwrite → open file A (popout shows A) → open file B → same popout switches to B.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79b31617f7e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.