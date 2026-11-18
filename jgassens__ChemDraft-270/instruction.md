# Issue

**Title:** Keep rotated objects whole in Copy As and Content exports

## Description

## Summary

Copy As (PNG, SVG) and the Export dialog's **Content** crop cut off rotated objects. The crop box was built from each object's unrotated frame. For example, a 2:1 picture rotated 90° lost 21% of its height, and one rotated 30° lost a strip on the left and the bottom. The **Page** crop was not affected.

`copyAsScopedDocument` (`apps/desktop/src/documentWorkflow.ts`) now builds the crop box from each object's rotated visual bounds, using the per-type helpers that already exist:
- graphics (pictures, art, paths, orbitals): `documentObjectVisualBounds` / `rotatedGraphicLocalBounds`;
- text, molecules with stored rotation, and tables: `textVisualBoundsForArrangement`, `moleculeVisualBoundsForArrangement`, `tableVisualBoundsForArrangement`;
- arrows, brackets and other objects: the frame corners rotated with `transformPointForObject`.

All of these rotate about the same centre the renderer uses. The 16-unit padding and the translation are unchanged. An unrotated document gets exactly the same crop and translation as before.

## Known limitations

- An arrow or bracket that is both tilted and rotated can still be cropped a little short: the crop applies the rotation but not the tilt projection. With no rotation, the crop is the same as before.
- Label, effect and table overflow count toward the crop only for rotated objects, so the crop box can grow a little between 0° and 1°. It is never smaller than before.

## Tests

- `apps/desktop/src/documentWorkflow.copyAs.test.ts` covers:
  - a 2:1 picture at 90° and at 30°, checked against its true rotated bounding box;
  - rotated text;
  - a molecule with stored rotation;
  - a 0° control whose page size and translation match the old behaviour exactly.
- Gauntlet on macOS at ea396346: `cargo fmt --check`, `cargo clippy --all-targets -D warnings`, `cargo test`, `pnpm lint`, `pnpm build` and `git diff --check` all pass. `pnpm vitest run`: 13451 passed. Two tests timed out under machine load and passed on their own (`perf/failOpen.test.ts`, `plugin-api/authoring3d.test.ts`).
- The branch has since taken two merges from main: #266 (the build stamp conflicted and `documentWorkflow.ts` merged automatically) and #267 (stamp only). Each merge was reviewed. CI covers the merged tip.

## Platforms

Shared TypeScript, with no platform-specific code.
- macOS: hands-on PASS at 0904954b, using Copy as PNG.
  - Picture rotated 90° and enlarged: the blue and orange halves are equal (606 and 605 px) and nothing is cut.
  - Picture rotated 30°: all corners are inside the image.
  - 0° control: framing unchanged.
  - Measured on the saved PNGs: no picture pixel touches any image edge.
- Windows: hands-on PASS at 0904954b. Copy as PNG kept the picture whole at 0°, 90° and 30°, and kept rotated text whole. The 0° framing is unchanged from main.

## Reviews

- Fix written by GPT-6.1 Sol (run-20261101-184040-0adcfa). The bug was found and traced read-only by Sol run-20261101-183351-7f81e4 on main.
- Claude Opus 5.5 run-20261101-184324-3f0fe7: approved; low notes are listed above.
- Claude Opus 5.5 run-20261101-191223-fe6ae9 (merge with #266) and run-20261101-192348-e5e0ed (merge with #267): both merges approved; neither changes the crop or the picture drawing.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a820ec27354`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.