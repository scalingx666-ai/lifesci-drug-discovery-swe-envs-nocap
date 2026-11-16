# Issue

**Title:** feat(viewer): VESTA-style view-angle panel with persistent default view

## Description

Adds a VESTA-style orientation workflow to the structure viewer. A new angle button in the toolbar opens a compact panel:

- **X/Y/Z view angles** (degrees, XYZ Euler order about the world axes) of the current view relative to the built-in default (camera on -Y, Z up). The readouts track the camera **live while dragging**; tracking pauses while an input has focus, and typing a value (Enter/blur) reorients the view exactly — orbit target and distance are preserved.
- **Lock** saves the current view direction + up vector to localStorage as the default view; **unlock** clears it (only shown when a default exists).

The saved view is passed to `StructureScene` as `initial_view`, so the scene's own initial camera placement — and camera reset — uses it directly for every structure opened afterwards (applying it after the fact raced the load/refit pipeline and got overwritten). Preview/readonly viewers (`persist_settings=false`) keep their fixed framing, so launcher sample cards are unaffected.

i18n: en/zh keys added in parity. `svelte-check` reports no errors in the touched files; the i18n parity test passes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `907bab8f34fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.