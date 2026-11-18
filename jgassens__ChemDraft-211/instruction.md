# Issue

**Title:** Clicking the canvas takes keyboard focus back from the assistant prompt, so Undo reaches the document

## Description

## Summary

When a plugin's canvas overlay prompt was open, clicking the canvas left keyboard focus in the prompt's textarea. Cmd/Ctrl+Z and Edit ▸ Undo then went to the textarea, so the document was not undone.

- A left or right press on the drawing surface moves keyboard focus from the overlay prompt to the canvas, so editing shortcuts and native Edit menu commands reach the document again.
- The handoff happens only when focus is inside the overlay. Presses inside the overlay, on the canvas scrollbars (always visible on Windows) or rulers, and middle, pen-barrel or secondary-touch presses keep the prompt focused, with no lost keystrokes. An active canvas text edit keeps its own focus.
- While the prompt is composing text with an input method (for example Japanese), canvas presses and scrollbar presses never take focus: the focus move is cancelled and the canvas cannot take focus until composition ends, so the composition is not cut off. A composition that never reports its end stops blocking after an idle timeout.
- The overlay's own behaviour is unchanged: focus returns to the prompt after an overlay button, the box takes focus only when clicked, Esc collapses it, and drafts are kept.

## Tests

- Real-event DOM tests (AGENTS.md §5) on both the macOS and Windows platform branches: a canvas click, then Cmd/Ctrl+Z undoes the document; overlay, scrollbar, corner, border and ruler presses keep the prompt focused (each test checks the precondition first); an active canvas text edit keeps focus.
- Composition: for all three composition signals (compositionstart, composing input, composing keydown), a scrollbar press and left and right canvas presses produce zero blur or focusout on the prompt, and the draft is kept. The tests emulate the engine's default focus move, so removing either guard makes them fail.
- macOS: `pnpm lint`, `pnpm build`, `git diff --check`, `pnpm vitest run`. Rust is unchanged.

## Platforms

- macOS: automated checks above. Hands-on input-method check pending.
- Windows: CI; hands-on, three of four checks pass. The input-method check could not run on the test VM (its Japanese input method does not compose) and is unverified on Windows.

Reviewed by claude-opus (eight reviews across the fix and its follow-ups).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91d48c610de0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.