# Issue

**Title:** Atom-label editor: size from the measured label, so OMe no longer crops to ▯me

## Description

## Summary

Typing a label such as **OMe** (also **Ome**, **Cl**) into the inline atom-label editor showed **▯me**: the first glyph was scrolled out of view.

**Cause.** `<input className="native-atom-label-editor">` was sized `${Math.max(1, draft.length + 0.6)}ch` (from 35646b3). `1ch` is the advance of "0" (0.556 em in Arial), but "O" is 0.778 em and "M" is 0.833 em. "OMe" got 2.0 em of box for 2.17 em of text, minus 2px of padding. The input overflowed and scrolled to keep the caret visible, which hid the start.

**Fix.** A new module, `atomLabelEditorWidth.ts`, measures the draft with canvas `measureText` in the editor's own font (family, size, weight and style from `labelStyle`) at the unscaled size. The resulting width is:

```
calc(<measured>px * var(--page-scale) + 0.6ch + 2px)
```

- The measured text scales with `--page-scale` exactly as the editor's `font-size` does.
- `2px` is the horizontal padding (the input is `border-box`).
- `0.6ch` is the caret room the old width already allowed. Being font-relative, it also absorbs sub-pixel differences between canvas and DOM text at every zoom.
- The editor stays centred on `atomLabelAnchorOffset`; its existing `translate(-50%, -50%)` is untouched.
- An empty draft keeps the inline `1ch` it had before. What shows is App.css's `min-width: 0.75em`, which is wider than `1ch` in the label fonts. The CSS is unchanged.
- Canvas behaves the same in WebKit and WebView2. CSS `field-sizing` was not used because WebKit lacks it.

**Fallbacks.** In both of these cases the width falls back to the old character count rather than measuring in the wrong font:
- No 2D canvas is available.
- The canvas rejects the label font. An imported family name that is not a CSS identifier makes the shorthand invalid, and a canvas then silently keeps its previous font, which is `10px sans-serif` when new. A sentinel font detects this.

`MainWindow.tsx` changes by an import, the width line, and the build stamp. The editor's `onBlur` line, which #77 edits, is 12 lines below; the only expected conflict with #77 is `CURRENT_BUILD_STAMP`.

## Files changed

- `apps/desktop/src/atomLabelEditorWidth.ts`: new. Canvas measuring context (`OffscreenCanvas`, else `<canvas>`; a missing context is remembered), the sentinel guard, the font shorthand, and the width.
- `apps/desktop/src/atomLabelEditorWidth.dom.test.ts`: new. 13 cases.
- `apps/desktop/src/MainWindow.tsx`: import, width line, `CURRENT_BUILD_STAMP` → `10.10.10.40-opus`.

## Tests run

- **The new test.** The canvas is stubbed with Arial advance widths and rejects unparseable fonts like a real one. The editor's CSS width is resolved numerically (px, ch, em, `var(--page-scale)`, `calc`, `max`, `min`). Cases:
  - "OMe" is wider than "ill", and the editor's anchor doesn't move as it grows.
  - The text plus a 1px caret fits the content box for OMe at 1 and 2.5, Cl at 1, CO2Et at 0.5 and 4, and a 31-character draft at 1.
  - Measurement uses the editor's own font, including a per-atom bold italic 20px label.
  - An empty draft's inline width is unchanged.
  - A rejected font falls back to `3.6ch`.
  - With no canvas, the width falls back to the character count.
- **Regression proof.** With the old width put back, 5 of the original 11 cases fail.
- **Gauntlet and WebView2 hands-on.** Results are in .

## Results

- **CI** is green on `7d84bcf`: Linux types, tests and web build; macOS Rust; Windows types, full tests and Rust.
- **Local Windows gauntlet:** lint, release build, `git diff --check`, `cargo fmt`, clippy (`-D warnings`) and `cargo test` pass. Local vitest showed 11 timeouts and races on an overloaded shared machine; CI's full Windows run is clean.
- **WebView2 hands-on:**
  - Live editor: 36/36 (9 labels × zoom 50% to 849%), with every glyph visible.
  - Canvas vs DOM: 48/48 across 8 font stacks, including Mac-only families that fall back.
  - Emulated IME composition: 4/4.
  - The Windows session's separate pass: 21/21.
- **Review:** claude-fable `fable-pr80-20261010`, APPROVE WITH NITS. The nits are fixed in `7d84bcf`, and the re-review `fable-pr80-rereview-20261010` is APPROVE.

## Platforms

- **Windows:** verified (WebView2 154).
- **macOS: unverified.** It needs the owner's hands-on check: OMe, Ome and WMW, every glyph visible, at 50%, 100% and 850% zoom.

## Known limitations

- **Real IME composition is unverified** on both platforms. Only emulated composition (DevTools `Input.imeSetComposition`) was checked.
- **An imported label family that is not a CSS identifier** (e.g. unquoted `3M Sans`) falls back to the old `ch` width, and "OMe" crops exactly as before the fix. Both the canvas and the input reject such a family. This was checked in WebView2; **WebKit is unverified for this path.**
- **#77's hover-typing entry point** opens the same input but can only be exercised once #77 merges. This PR checked the Atom Label tool press.
- Zoom bottoms out at 50% (`viewport-engine` `minZoom`), not 25%.

## One recommended next task

None proposed here; follow-ups go through the coordinator.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcb5357b05ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.