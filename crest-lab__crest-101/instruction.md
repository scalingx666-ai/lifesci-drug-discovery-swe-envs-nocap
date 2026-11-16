# Issue

**Title:** Bugfix: wrong MD time step

## Description

Fixes a bug introduced in #90 that reduced the MD and MTD time step and led to increased computation times.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84541b5dab3f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.