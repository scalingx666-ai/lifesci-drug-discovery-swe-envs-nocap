# Issue

**Title:** Focus the canvas on a click when nothing else has focus

## Description

## Summary
A click on the page or empty canvas left keyboard focus on the page body (page tools cancel the default focus change), so canvas shortcuts and the context-menu keys did nothing after launch or after a dialog closed until something else returned focus (found on Windows with a real mouse).

A primary pointerdown on the page now focuses the canvas region **only when nothing is focused** (body or root), and never:
- from an editable target (text fields, the text-object editor);
- behind a modal prompt;
- while an IME composition is in progress.

Composition is tracked passively (no key is consumed or redirected). The guard ends on `compositionend`, `compositioncancel`, a non-composing key or input, or a 10-second idle timeout now shared with the plugin canvas overlay (`ORPHANED_COMPOSITION_IDLE_MS` in `apps/desktop/src/imeComposition.ts`). Moving focus away during a composition does not end it. Tab order, keyboard handlers and the assistant-prompt focus behaviour (#211) are unchanged. The scope is deliberately narrow after the parked composition-guard attempt (#214).

## Tests
- `MainWindow.canvasFocus.dom.test.tsx` (real DOM focus, macOS and Windows platform variants): BODY focus → canvas focus on click; no focus theft from fields, the text editor, the overlay prompt, menus or behind a modal; composition blocks focus and every recovery path (end, cancel, non-composing key/input, idle timeout, blur-then-cancel) re-enables it.
- `MainWindow.plugins.dom.test.tsx`: an overlay prompt composition followed by blur does not hand focus to the canvas until the composition ends.
- Lint OK; MainWindow, canvasContextMenu and plugins suites 1547 passed in repeated runs; full vitest 9952 passed (2 failures in `tools/agent-skill/stress/runner`, which passes 57/57 alone here and on main, logged separately). No Rust changes.
- `docs/manual-stress-checklist.md`: one short real-Japanese-IME pass per platform.

## Platforms
- macOS and Windows: hands-on pending (one short Japanese-IME pass each: one Return commits, click empty page, type again; plus a click on empty page then Shift+F10 / shortcuts after launch and after a dialog closes).

Reviewed by Kimi K3 (changes requested, fixed) and Claude Opus (no blocking findings).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5007cf785d07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.