# Issue

**Title:** Allow pd.Series input to filter

## Description

filter_elements, e.g. SMARTS, could not be provided as `pd.Series`. Now they can.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `937edd64a0cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.