# Issue

**Title:** Switching document mid-drag releases the drag's own pointer capture

## Description

. Switching document or tab during a drag now releases the drag's own pointer capture.

**The bug:** #125 records which element took each drag's pointer capture (an object, a handle, or the page), so Escape releases it there. Pointer capture means that element receives every pointer event until the drag ends. A document or tab switch mid-drag still released capture only on the page and the canvas region. A drag that had captured on an object or handle kept sending pointer events to that element until the button came up.

**The fix** (`cancelDocumentTabSessions` in `apps/desktop/src/MainWindow.tsx`): each document gesture the switch cancels releases its recorded capture owner through `releaseGesturePointer`, and the page and canvas-region release stays as a fallback. A floating web palette's drag is left alone: the switch deliberately keeps it, and an earlier version of this fix broke it (caught in review).

**Tests** (`apps/desktop/src/documentSwitchCapture.dom.test.ts`)
- An object move, a handle drag and a marquee each move first, then the tab is switched. Each capture is released once, and later move and up events on the new page change neither document.
- A palette drag survives a tab switch.
- With a document drag on one pointer and a palette drag on another, only the document drag's capture is released.
- Both palette tests fail without the fix.

**Reviews:** Sol blocked round 1 (palette capture released); round 2 APPROVE.

**Platforms:** macOS: tests (Mac packaged check with #125). Windows: steps 1–4 PASS on 10.12.03.05-opus (CDP input; no regression).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b106c48c631`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.