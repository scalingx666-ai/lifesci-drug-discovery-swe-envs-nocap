# Issue

**Title:** Floating toolbars and panels show an edge when they overlap; document tabs are rounded and tinted

## Description

**Pending:** the owner's verdict on the toolbar look, and the Windows hands-on run. Not to be merged before both.

## Summary
- Floating toolbars and plugin panels get the native drop shadow that the colour-picker popover already has (`.shadow(false)` → `.shadow(true)` in the two window builders; nothing else in the builders changed).
- An inset highlight and outline drawn on the toolbar window shell, so stacked toolbars keep a visible edge at any size or orientation. The CSS is additive: new tokens and new scoped rules at the end of `App.css`, with no existing palette rule rewritten.
- Document tabs: rounded top corners and a faint outline. The active tab is accent-tinted, with an accent bottom bar and a small lift. Inactive tabs have a hover state. focus-visible is unchanged.

## Files changed
- `apps/desktop/src-tauri/src/lib.rs`: native shadow on for the toolset palette and plugin panel windows
- `apps/desktop/src/App.css`: edge tokens, shell edge rules, tab styling
- `apps/desktop/src/paletteDepth.test.ts`: new tests pinning the rules and the shadow flags
- `apps/desktop/src/MainWindow.tsx`: build stamp

## Tests run
fmt, clippy `-D warnings`, cargo test (268 passed), full vitest (6823 passed, 0 failed), `pnpm lint`, `git diff --check`: all pass.

## Review
openai-astra (run rvdepth-20261013): APPROVE, no findings.

## Platforms
- **macOS: verified** on a packaged branch build (10.13.17.38-codex). Overlapping toolbars show an outline and a shadow; the Main toolbar over the canvas shows its edge; after the native Open dialog the toolbars return in the same stacking order. The tabs were checked live by the owner.
- **Windows: unverified.** To check: the 1 px DWM border that `shadow(true)` adds (a possible double edge with the inset outline), Windows 11 corner rounding, resize hit regions, toolbars and panels staying off the taskbar and not taking focus, and stacking after minimize/restore.

## Known limitations
- Shadow redraw after a user resize or reorientation can only be checked once #112 (resizable toolbars) lands.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ec8f7cfefeb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.