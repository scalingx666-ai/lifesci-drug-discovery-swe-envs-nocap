# Issue

**Title:** Some fixes and code optimization

## Description

1. Added argument of batch size.
2. Fixed a bug that a too long ligand would cause the file path length to exceed the limit and fail to save.
3. Fixed a bug that the amount of molecules generated does not match the argument set by user.
4. Optimized some code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `127e6a149c94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.