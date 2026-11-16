# Issue

**Title:** Clean up ConformerGenerator keyword args

## Description

This PR  by validating that integer arguments to `ConformerGenerator` are indeed integers. It also removes an unused keyword from `run`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d6bc6425cc1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.