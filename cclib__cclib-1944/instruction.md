# Issue

**Title:** Merge `master` into `release-1.9`

## Description

This is primarily to fix CI on the release branch via

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `545fa9bdd25a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.