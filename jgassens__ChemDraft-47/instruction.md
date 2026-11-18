# Issue

**Title:** Fix label typing being erased; make Edit ▸ Undo/Redo undo the drawing

## Description

Fixes two problems from tester feedback.

## 1. Typed substituent labels "kept getting erased"
When the atom-label box lost focus mid-typing, the edited atom stayed **selected**, so the rest of the typed letters went to canvas hotkeys: `e` armed the eraser, element letters (O, N, C…) overwrote the label with a single atom, Backspace stripped it.

- The pre-edit selection is restored whenever a label edit closes by any path except Enter/Tab/Escape (including a tool picked from a palette).
- The label box shares the text editor's focus hardening; Tab finishes like Enter; a blur caused only by the window going inactive (a palette taking key status) keeps the edit open.
- Back-to-back edits carry over the first edit's selection; focus-retry timers are cleaned up.

## 2. No working Undo in the menu
Edit ▸ Undo/Redo were AppKit's predefined items, which send `undo:` to the web view's text undo manager and never reached the drawing's history (⌘Z worked only via the JS shortcut). They are now routed `edit.undo` / `edit.redo` items, still showing **⌘Z / ⇧⌘Z**, delivered to the key window:
- a focused text-entry field gets native text undo;
- otherwise the drawing is undone; secondary windows forward to the main window with a marker that forces drawing history.
- No toolbar change (owner decision).

## Not addressed
"Had to click multiple times to draw benzene" — no confirmed cause from code reading; needs the tester's answer (did the ring flash and vanish, or never appear?).

## Verification
- `pnpm lint`; `pnpm vitest run` — 3514 passed, 16 skipped
- `cargo fmt --check`, `cargo clippy --all-targets -D warnings`, `cargo test --lib` — 72 passed, 1 ignored
- build-stamp script passes (`9.24.23.16-sonnet`)
- `./run-app --dev` from this worktree launched (port 5174, bundle `org.chemdraft.desktop.dev.tester-fixes`); accessibility read of the live Edit menu shows `Undo ⌘Z`, `Redo ⇧⌘Z`, enabled.
- **Not yet checked by hand in the live app:** one ⌘Z press = one undo on the canvas; ⌘Z inside the label box undoes text only; ⌘Z in a palette search box undoes its text; typing half a label, clicking a palette, clicking back and continuing.

Implemented by Claude Opus/Sonnet workers; reviewed twice by Claude Opus (findings fixed in the second and third commits).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ec147c2f513`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.