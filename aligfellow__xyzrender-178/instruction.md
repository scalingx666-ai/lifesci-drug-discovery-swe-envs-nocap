# Issue

**Title:** Fix trajectory GIF orientation and worker hangs

## Description

Trajectory GIFs now preserve input coordinates when auto-orientation is disabled and use the matching frame for explicit orientation references.

This also prevents GIF rendering from hanging when called through stdin and makes worker failures propagate to the caller.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b80f65a1b60e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.