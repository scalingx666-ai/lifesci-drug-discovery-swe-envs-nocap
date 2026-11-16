# Issue

**Title:** Ensure background rectangle is correctly sized.

## Description

Now AWTDrawVisitor was updated to scale rectangles correctly, these values were not correct in the buffered image generate.

The SVG ones can also be simplified

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e3c86929677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.