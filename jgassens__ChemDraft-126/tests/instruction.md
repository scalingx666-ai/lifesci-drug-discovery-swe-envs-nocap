# Issue

**Title:** Shapes: the corner-radius handle no longer covers the corner resize handle

## Description

**Visual change: waiting for the owner's look before merge.**

With a square corner, a shape's corner-radius handle sat about 1 px from the top-left resize handle and took the press, so the shape could not be resized from that corner. It happened at every size, on both platforms; the Windows session confirmed it on main.

**What changes**
- At radius 0 the radius handle sits a fixed **16.5 screen pixels** along the top edge from the corner, at any zoom. That is the resize handle's reach (18 px target, −8 px offset), half the 9 px radius handle, and a 2 px gap. Past that distance the handle follows the real radius as before. The `Radius: N px` readout stays at the real radius point.
- The radius drag adds the pointer's travel to the starting radius, so pressing the moved handle causes no jump and the drag feels the same.
- **Placement rules.** A spot counts as usable when the handle's centre is on the page and its box clears every resize target, checked on the projected boxes so tilted shapes work. Spots are tried in order:
  1. inside along the top edge;
  2. past the controlled corner;
  3. past the opposite top corner;
  4. the short stretches just outside each corner.

  If nothing is clear, the visible spot with the most clearance wins.
- **Zoom.** Only the selected shape that shows the handle receives the zoom scale, so other objects do not re-render on zoom. A DOM test checks this.
- **Shared helpers.** The rotation and frame helpers move from `MainWindow.tsx` into `apps/desktop/src/graphicHandleGeometry.ts`, unchanged for their existing callers, with the handle sizes App.css uses.

**Known limitations**
- While a shape is being dragged, the handle's placement is not recomputed until release, so it can briefly sit off the page. It cannot be grabbed mid-drag, and it snaps back on release.
- A shape sliding across a page edge can make the handle hop between the inside spot and an outside spot.

**Tests:** placement unit tests (radius 0, small and large radii, small shapes, rotation, tilt, page edges, the narrow-page case, continuity), and DOM tests (resize and radius both start from their own handles at radius 0, no jump, clamping, negative travel, no re-render of unselected objects on zoom). Lint and the full suite pass.

**Reviews:**
- Astra blocked round 1: zoom re-rendered every object, and small shapes could be clipped off the page.
- Round 2 blocked: whole-handle-on-page fell back to mid-edge at page edges.
- Round 3 blocked: the narrow-page fallback.
- Round 4: APPROVE.

**Platforms:** macOS: tests; packaged check and the owner's look in the morning. Windows: hands-on run requested.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23eae6b9d2d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.