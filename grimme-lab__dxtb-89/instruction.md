# Issue

**Title:** Version-specific `torch.scatter_reduce`

## Description

Adapt `torch.sactter_reduce` to run for PyTorch versions 1.11.0, 1.12.0, 1.12.1, and 1.13.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `095635f73634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.