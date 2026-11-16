# Issue

**Title:** Fix NumericalTarget constructor calls

## Description

* Adds the missing minimize flag to `match_absolute` / `match_power` and corresponding tests
* Fixes the constructor call in `from_modern_interface`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fc99d50c99f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.