# Issue

**Title:** Allow caching of restart data

## Description

- implement caching of API calculator object within the ASE calculator
- invalidation of cached API calculator is performed on basis of the `system_changed` list
- changes like `"positions"` and `"cell"` allow to update the molecular structure data

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b58c180f388c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.