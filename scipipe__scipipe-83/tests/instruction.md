# Issue

**Title:** Add select based Task processing.

## Description

This avoids the deadlock condition of #81 and removes the limit of BUFSIZE concurrent Tasks per Process introduced by #82.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `359427b21929`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.