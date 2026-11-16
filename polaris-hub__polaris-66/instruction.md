# Issue

**Title:** remove nans

## Description

This is to solve the issue when validate and compute `type_of_target` for datasets containing NaNs (for the  sparse datasets with multi targets).

## Changelogs
- Remove nans from dataset when check the target type.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae0151b53eb1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.