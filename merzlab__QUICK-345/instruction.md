# Issue

**Title:** Add error checks for builds enabling f-functions with GPU targets requiring legacy atomics (-DUSE_LEGACY_ATOMICS).

## Description

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2257ba84f5ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.