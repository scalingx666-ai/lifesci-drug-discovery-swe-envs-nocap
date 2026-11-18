# Issue

**Title:** Skip the native palette reconcile off the desktop runtime (fixes an unknownBondOrder flake)

## Description

## Summary

**The flake.** `unknownBondOrder.test.ts › refuses an overlay flatten after unknown bond order and commits nothing` failed twice under full-suite load on the Windows machine. Its status line read "Native toolset windows unavailable; using in-window toolbars", not "Cannot flatten this view: …".

**The cause.** The test mounts `MainWindow` with `nativePalette: true`, as 19 DOM test files do. Native palette windows exist only in the desktop runtime, and the app only turns native palettes on by default there (`shouldDefaultToNativePalettes`). With no desktop runtime the native reconcile still ran:
- `listToolsetWindowStates` called Tauri `invoke`, which isn't there, so all three attempts failed, 200 ms apart.
- The app then switched to in-window toolbars and posted the fallback status over whatever the status line said at that moment.
- About 0.4 s after mount is usually before a test asserts anything. Under load it landed mid-test.

**The fix.** The reconcile effect returns early when `isDesktopRuntime()` is false: there is no window manager to reconcile with. It is not a retry or a longer wait.
- The desktop app is unchanged. It still reconciles, and it still falls back when native windows genuinely fail; `reconcileNativePalettes.test.ts` covers that outcome.
- Off the desktop runtime, native palettes come on only when a caller forces them.

## Files changed

- `apps/desktop/src/MainWindow.tsx`:
  - the early return in the native palette reconcile effect;
  - a doc comment on the `nativePalette` prop (76dcb98). It defaults on only in the desktop runtime, nothing in the app turns it on elsewhere, and forcing it on off the desktop runtime, as tests do, runs native mode with no window manager and no in-window palettes either;
  - `CURRENT_BUILD_STAMP` is `10.10.21.21-opus`.
- `apps/desktop/src/nativePaletteOffDesktop.dom.test.ts` (new): a deterministic repro. It mounts with `nativePalette: true` and no Tauri runtime, posts a status ("Blank native document"), then advances fake timers well past the retry window and expects the status line unchanged. On the previous code it fails with exactly the flake's message: `expected 'Native toolset windows unavailable; using in-window toolbars' to be 'Blank native document'`.

## Tests run (Windows 11)

- `pnpm lint`: pass.
- `git diff --check`: pass.
- The repro: fails on 8be1612, passes on this branch.
- `unknownBondOrder.test.ts`, `reconcileNativePalettes.test.ts` and the repro: 37 passed.
- All 19 test files that mount with `nativePalette: true`: **490 passed**, so none depended on the fallback appearing.
- Full suite (`pnpm vitest run`, 76dcb98): **279 files, 5,321 tests passed, 0 failed** (33 skipped), including `unknownBondOrder.test.ts`.
- No Rust changes.

## Platforms

- **Windows:** verified as above. The change is test-environment behaviour only; the desktop runtime path is unchanged, so there is no launched-app difference to check.
- **macOS:** unverified. The change is shared TypeScript with no platform branch.

## Known limitations

None: the fallback for a genuine native failure is untouched.

## Review

## One recommended next task

None from this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4dfe40d17e90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.