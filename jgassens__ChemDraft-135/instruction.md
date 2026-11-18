# Issue

**Title:** Molecule moves preview with a transform instead of re-rendering every frame

## Description

Dragging a selection of molecules re-rendered every moved molecule on every pointer move. On a page of 256 rings that was about 41 000 DOM nodes per frame. Now molecule and mixed moves slide the painted molecules with a CSS transform during the drag, and render once on release.

**Measured**
- jsdom: 323 → 5.5 ms per frame on 256 rings.
- Windows packaged build: 625 → 56 ms per move; a whole drag went from 13.2 to 1.9 s; release takes 0.57 s.
- The drop lands within 1 px, as one undo step.

**What changes**
- During the drag, the moved molecules (and anchored mechanism arrows that follow them) are shown as a transform preview; the document changes once, on release.
- The preview cancels cleanly on Escape, a tab switch, undo mid-drag and window blur. Blur resets the modifier keys only, as before.
- Anchored arrows use one frame rule. At rest they take #128's resolved bounds. During a transform move they take the preview's own bounds, so the selection box and handles stay on the arrow.

**Visible difference (the owner looked at this on 2026-10-12 and approved):** bond-crossing gaps travel with the moved molecules, and new crossings show no gap until release.

**History.** This was built and tested on the morning's combined branch. Astra blocked round 1 (tab switch, undo mid-drag, anchored-arrow controls) and approved round 2. A blur-cancels-drag addition broke an existing contract and was reverted (Astra APPROVE). The reconciliation with #128, 7251717, was written by Sol (arrow-drag-integration-20261012) and approved by Astra (arrow-drag-review-20261012). This PR ports those five commits onto main, now that #109, #124, #125 and #128 have landed. In the arrow test, main's stricter assertions are kept.

**Tests:** lint ✓; dragTransform, dragPerf, mechanismArrowBounds, textObjectEdit, textOnShape, graphicPathEdit and tabs suites: 251 passed, 1 skipped.

**Platforms:** Windows measured and checked on the combined build (10.12.04.50-opus). A re-run on this port and a Mac check are pending.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de41894ba9ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.