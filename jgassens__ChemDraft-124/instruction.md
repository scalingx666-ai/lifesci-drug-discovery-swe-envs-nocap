# Issue

**Title:** Large pages: drags and undo stop searching for dialogs; release skips a redraw

## Description

## Summary

Profiling a page of 256 overlapping benzene rings (dragging it took 7.2 s on Windows) found, besides re-rendering every moved molecule per frame (a larger fix that waits for #109):

- **Modal-dialog searches:** every drag frame searched the whole page twice for an open modal dialog (modifier-key hints and the shortcut guard), and every undo five times.
- **Redundant release redraw:** releasing a drag rebuilt the moved document once more although the last preview already had it.

The "is a modal dialog open?" answer is now kept up to date as dialogs open and close, with the same blocking of shortcuts and clipboard actions, and modifier hints refresh only when their inputs change. A release whose position matches the last preview commits that preview. Documents produced by drags and undo are unchanged.

Measured on Windows (WebView2), 256-ring page, with #123's crossing fix also applied: **release 478 → 47 ms**; whole drag 6.7 → 6.2 s (each pointer move is still ~0.6 s, dominated by re-rendering every moved molecule, which needs a separate fix after #109); undo/redo ~5% faster. (jsdom showed larger gains for the dialog searches than the real webview does.)

## Files changed

- `packages/shortcut-engine/src/index.ts`: cached modal-open state.
- `apps/desktop/src/MainWindow.tsx`, `documentWorkflow.ts`: hint refresh, preview reuse on release.
- Tests: `MainWindow.dragPerf.dom.test.ts` (new), `shortcut-engine/src/index.test.ts`.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 309 files, 6147 tests pass

## Platforms

- Windows ✓ (shortcuts blocked while a dialog is open, unblocked after; modifier hints update; timings above)
- macOS: check to follow

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13b7cc762c12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.