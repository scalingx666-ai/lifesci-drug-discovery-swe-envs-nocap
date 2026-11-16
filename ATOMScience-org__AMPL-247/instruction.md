# Issue

**Title:** need to transform dataset before using it

## Description

Transfer learning with a base model using mordred_filtered features was producing nan predictions. Dataset preparation skipped a set that set nans in mordred features, which is totally normal, to zeros.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e6b79beb6f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.