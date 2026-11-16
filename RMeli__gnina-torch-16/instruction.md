# Issue

**Title:** Add high-resolution models

## Description

Add `HiResPose` and `HiResAffinity` models. They only work for combined pose and binding affinity prediction.

This PR also removes spurious double computations of the pose score in some models.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c5da04f0060`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.