# Issue

**Title:** Hide toolbar tooltips while a popover is open; readable select lists on Windows

## Description

## Summary
Two toolbar overlay problems found while testing the 3- to 8-membered ring flyout (#262):

- **Tooltips over or under an open popover.** While a toolbar popover is open (a flyout, the art colour picker or the E/Z note), the shared palette tooltip no longer shows, on macOS or Windows. Revealing a popover hides any tooltip first (best-effort, so a failed hide never blocks the popover), and tooltip shows are refused until the popover closes; tooltips return on the next hover. Before this, a tooltip such as "Resonance Arrow" drew over the open flyout on Windows (popovers and the tooltip are both raised to the top of the document's owned windows, so the later one wins) and partly under it on macOS (popovers sit one level above the palettes since #262). Window ordering, levels, ownership and focus are unchanged; nothing becomes topmost.
- **Black select lists on Windows.** The Art toolbar's paint-type list (showing "None") opened as a solid black list in WebView2. Toolbar selects and the Molecule and Ring inspector selects now share one rule declaring a light colour scheme with opaque option colours from the existing light tokens. The closed controls look as before; the app has no dark theme.

Escape closing a mouse-opened popover was considered and left out: doing it safely needs shared popover state and coordination with several capture-phase key handlers. It stays a logged follow-up, as do select lists in dialogs and plugin panels (to be checked on Windows) and drag-release selection in flyouts.

## Files changed
- `apps/desktop/src-tauri/src/lib.rs`: tooltip suppression while a `toolset-popover-*` window is visible (guard in the native tooltip show path; an unreadable visibility counts as hidden), best-effort tooltip hide before a popover is revealed; a Rust test.
- `apps/desktop/src/App.css`: shared light colour scheme and option colours for toolbar and inspector selects.
- `apps/desktop/src/PaletteTooltipWindow.policy.test.ts`: regression checks for the guard, the hide, and the select rules.
- `docs/manual-stress-checklist.md`: hands-on entry naming the covered selects and the tooltip behaviour.
- `apps/desktop/src/MainWindow.tsx`: build stamp.

## Tests run
Focused vitest (PaletteTooltipWindow policy and tooltip tests, commandSeparation), `cargo test` (tooltip suppression), clippy `-D warnings`, `cargo fmt --check`, and the full gauntlet: all green at 5637f6a8 (after a catch-up with main 26faaf37): pnpm lint, pnpm build, git diff --check, cargo fmt, cargo test; pnpm vitest run 14452 passed with 6 load timeouts on a just-restarted machine (AssistantToolsController 5000-molecule, pdf 16.8 MB PNG, ocl-adapter progressive, stress runner) that passed on a rerun of those 4 files (260/260); cargo clippy -D warnings passed on a rerun after a stale Sparkle link from another worktree had stopped its build script. Build-only macOS bundle built, stamp 11.01.21.08-opus.

Reviews: Opus (two passes) on the fix, Astra on the catch-up merge.

## Platforms
- **macOS:** PASS, 6/6 hands-on steps at 5637f6a8 (stamp 11.01.21.08-opus), 2026-11-02: tooltips normal with nothing open; none while the ring flyout or the art colour picker is open, and they return after it closes; the paint-type and arrowhead lists are light and readable and still apply; focus stays in the document (a placed ring undoes with Cmd+Z).
- **Windows:** PASS, 7/7 hands-on steps at 5637f6a8 (stamp 11.01.21.08-opus), 2026-11-02, including the paint-type list (light and readable) and every dialog and panel select list (all readable, none black).
- CI: macOS, Linux and Windows jobs.

## Known limitations
Esc does not close a mouse-opened popover (pre-existing). Selects in dialogs and plugin panels are not changed here; on Windows they were checked and are readable.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26faaf374e53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.