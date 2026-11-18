# Issue

**Title:** Plugin canvas overlay refits to a smaller window, resizes on a fast drag, and its header is not selectable

## Description

## Summary

Three fixes to the plugin canvas overlay (the icon that expands into a prompt box inside the document viewport), found in a Windows hands-on check:

- **Refits to a smaller window.** With the document window shrunk (for example innerHeight 405), a taller expanded overlay extended past the viewport, and its prompt row could not be reached. Fitting overwrote the remembered height and ignored window clipping and scale changes. Now the displayed height is never larger than what fits, the prompt row stays reachable, and the remembered height returns when there is room again. This applies on window resize, viewport resize and display-scale changes.
- **Fast drags on the resize grip resize.** Moves outside the 6 px grip could bypass its handlers. The drag now follows the captured pointer, with a document fallback, and ends on pointerup, cancel, lost capture, blur, collapse or hide, so it is never left stuck in resize mode.
- **Double-clicking the header no longer selects the overlay's text.** The earlier mousedown guard never ran in real webviews, because the cancelled pointerdown suppresses mousedown. Selection is now blocked where the browser starts it (selectstart), with a double-click backstop. The prompt and transcript stay selectable.

- **Remembers positions properly.** A refit changes only where the overlay is *shown*. The remembered position changes only when the user drags the overlay or uses the header reset, so growing the window brings it back. The stored position is versioned and records whether the user placed it. Positions saved by earlier builds (which saved refit-clamped positions, as `main` does) are discarded once, and the overlay re-docks. Malformed storage falls back to docked, and resizing writes nothing.
- **Launchers from several plugins never overlap.** Each plugin's launcher gets its own docked slot, ordered by plugin id, and stays clamped and reachable.

On `main` the overlay and launcher do not refit at all: at innerHeight 305 the launcher is off-screen and cannot be reached.

## Known limits

- A docked expanded overlay at a **top** corner no longer moves its top edge when the header is dragged; it shrinks from the bottom instead. Bottom corners, the default, are unaffected.
- After a shrink, a user-placed launcher can partly overlap a docked one until the window grows again. Part of the docked launcher stays clickable.
- A freshly expanded docked overlay can cover other launchers in its corner until it is collapsed, as on `main`.

## Tests

- DOM tests for refit on window shrink, viewport resize and scale change, with the remembered height restored. Also: fast drags with moves far outside the grip, pointercancel and lost capture, and selection using the real event order (cancelled pointerdown, no mousedown, then selectstart). Prompt-textarea selection still works.
- macOS: `pnpm lint`, `pnpm vitest run apps/desktop/src/plugins` (1114 passed with the main-window suite), `git diff --check`. A manual checklist line for both platforms.

## Platforms

- Windows: CI. The hands-on checks of the window clip, flick-drag and header double-click passed on dd29954f. Still to recheck: shrink, grow, relaunch, and two plugins' launchers.
- macOS: automated checks above. Hands-on check of the refit in a small window.

Reviewed by claude-opus (three rounds).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b0837df4282`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.