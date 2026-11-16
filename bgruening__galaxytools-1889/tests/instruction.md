# Issue

**Title:** New tool: Edit Coco Annotation

## Description

### Features

- Filters and renames tracks in a COCO JSON annotation file produced by SAM3 or any COCO-format
  - Mode Keep: only the listed track IDs are kept; all others are removed (+ optional: rename | frame_min | frame_max)
  - Mode Remove: only the listed track IDs are deleted; everything else is kept (+ optional: frame_min | frame_max)
  - Mode Rename: all tracks are kept, but listed IDs receive a new category name

### Tests

Test 1: keep mode — keep track IDs 2, 4–6 and track ID 1 renamed to "Algae"
Test 2: remove mode — remove track ID 1 from frame 130 onwards
Test 3: rename mode — rename track ID 1 to "Algae" and track IDs 2–6 to "Crangon crangon"

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b7c3d6d47bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.