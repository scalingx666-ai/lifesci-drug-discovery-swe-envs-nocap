# Issue

**Title:** Image Export Resolution and Size Stabilized

## Description

## Summary

Fix high-DPI PNG crop export so the exported image matches the user-selected crop window, and ensure exported PNG files carry the requested DPI metadata.

## What changed

- Fixed cropped high-DPI structure export:
  - Previously, CatGo rendered the full high-resolution canvas first and then cropped from it.
  - At 600 DPI this could hit WebGL size limits / scaling differences, causing the exported image to shift or get clipped.
  - Now cropped exports render the selected sub-view directly, keeping the output aligned with the on-screen crop box.

- Added PNG DPI metadata:
  - PNG exports now write a standard `pHYs` chunk.
  - The DPI entered in the UI should now match what image properties/readers report.

- Added a small helper script:
  - `scripts/check_png_dpi.py`
  - Can be used to verify PNG DPI metadata from the command line.

- Added regression tests for:
  - High-DPI crop render planning.
  - PNG DPI metadata insertion/replacement.

## Validation

```bash
node_modules\.bin\vitest.cmd run tests\vitest\io\export.test.ts
node_modules\.bin\vitest.cmd run tests\vitest\structure\StructureExportPane.test.ts

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b45435ccbfd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.