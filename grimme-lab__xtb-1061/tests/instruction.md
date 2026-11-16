# Issue

**Title:** Fixes #1054 by ensuring thread savety of hessian calculations with GFN-FF

## Description

The distance array neigh%distances was not allocated thread save and was removed from the neigh class.
Now the distances are calculated from the atom coordinates and the translation vectors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d55ea9b2626`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.