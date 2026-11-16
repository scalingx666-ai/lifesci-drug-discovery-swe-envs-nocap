# Issue

**Title:** Coco visualizer h264

## Description

I pushed a test on Galaxy Europe and see that the output video could not be played by media player, as the codec was not supported. So, following the same approach as SAM3, I add a re-encoding step.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b7c3d6d47bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.