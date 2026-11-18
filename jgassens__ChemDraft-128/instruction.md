# Issue

**Title:** Mechanism arrows: the selection box follows the arrow after its atom moves

## Description

A mechanism arrow anchored to atoms is redrawn from its anchors when the molecule moves, but its selection box and marquee bounds stayed where the arrow used to be. They came from the bounds stored on the object. Found on Windows; main does the same.

**Fix** (`apps/desktop/src/documentWorkflow.ts`, `MainWindow.tsx`)
- Interaction bounds now come from the same resolved arrow geometry the renderer uses (`mechanismArrowGeometry`), with the existing padded-frame convention. No rendering math is copied.
- The frame rotates around the same pivot as the arrow's SVG, so a rotated arrow's handles stay on its curve after its anchor moves.
- Resolved bounds and their lookups are cached per page snapshot. A marquee or lasso no longer recomputes every arrow on each step; any edit or undo makes a new snapshot.
- Anchors, chemistry and the move's single undo entry are unchanged.

**Tests**
- Unit and DOM: after an anchored molecule moves, the arrow's selection box matches the redrawn curve, and undo restores both.
- A marquee around the new position selects the arrow; one around the old position does not.
- A rotated arrow's handles coincide with its SVG controls.
- The cache is invalidated after a move.
- The DOM test fails on main at the move step.

**Not changed:** page-fit content bounds still use stored rectangles. That is pre-existing and noted for later.

**Reviews:** Astra blocked round 1 (rotation pivot); round 2 APPROVE.

**Platforms:** macOS: tests; packaged check in the morning. Windows: hands-on run requested.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ebc5aed5ad2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.