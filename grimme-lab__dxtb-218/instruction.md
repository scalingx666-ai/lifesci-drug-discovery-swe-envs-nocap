# Issue

**Title:** Make charge and spin always 1D

## Description

Shape of charge and spin tensors is now:
- `(1,)` for single system
- `(n, 1)` for a batch of `n` systems

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `acf3937fb463`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.