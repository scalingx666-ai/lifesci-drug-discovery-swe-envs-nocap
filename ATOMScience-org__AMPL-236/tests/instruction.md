# Issue

**Title:** Compound IDs should always be explicitly treated as strings.

## Description

Otherwise, they might be treated as ints and merging/inclusion/comparisons will not work correctly

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e69e1fc648f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.