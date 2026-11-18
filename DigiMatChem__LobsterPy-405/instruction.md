# Issue

**Title:** update test durations

## Description

### Issue

Test durations are not updated automatically as expected.

### Fix

Adds missing `--store-durations` arg to tests ci tests workflow

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e244e2fd8ee7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.