# Issue

**Title:** 211 make linters more strict

## Description

- "PD011",   # Use `.to_numpy()` instead of `.values`
 - "T201",    # print found

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90933ef86535`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.