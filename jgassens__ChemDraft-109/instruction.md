# Issue

**Title:** Canvas: paint every object in document order, like the export

## Description

## Summary

The canvas now paints every object in document order (`page.objects`), the same order the SVG/PDF export uses. Before, native molecules painted in their own canvas layers above the page SVG, so the canvas could stack objects differently from the file:

- text in front of a shape (or after Bring to Front) was hidden under it on the canvas;
- a molecule's ring fills covered text and ring letters placed on them;
- curved arrows, lone pairs and plus signs drawn over a filled ring were covered.

Bring to Front, Bring Forward, Send Backward and Send to Back now change the canvas and the export alike. Consecutive non-molecule objects share one layer, so pages with hundreds of labels stay light. Clicks, hover and menus go to the object on top, and colour previews update the visible drawing.

Replaces the approach in #107 (closed). Builds on unmerged work from 2026-10-09 (`review/canvas-ring-layering`).

**Held for the owner's look before merging** (visual change).

## Files changed

- `apps/desktop/src/MainWindow.tsx`, `App.css`: canvas layering follows document order.
- `apps/desktop/src/agentBridge.ts`: SVG capture follows the new layering.
- `apps/desktop/src/ringFillLayering.dom.test.ts` (new) plus updated `App.test.ts`, `agentBridge.test.ts`, `graphicPathEdit.dom.test.ts`.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 307 files, 6141 tests pass

## Platforms

- macOS: packaged build with before/after screenshots to follow
- Windows: real-input run to follow

## Known limitations

jsdom can't prove browser hit testing or compositing; the packaged builds on both platforms are the check for that.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e35da85df4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.