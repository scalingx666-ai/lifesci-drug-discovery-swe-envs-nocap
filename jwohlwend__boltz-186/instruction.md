# Issue

**Title:** fix random_subset logit for MSA subsampling

## Description

- Fixes a bug for featurizing a `random_subset` of the MSA. `indices` now returns as an iterable of size (max_seqs - 1).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bfa48f95f8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.