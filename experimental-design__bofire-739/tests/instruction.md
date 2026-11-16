# Issue

**Title:** Feature/pre compute tanimoto2

## Description

-- Simpler implementation of #701 --

Tanimoto-similarities are computed upfront, now in new surrogate `TanimotoGPSurrogate`

This avoids re-computation during model training and evaluation and excessive memory usage

computation is done in kernel, cov-tensors are passed to the strategy via `re_init_kwargs`

Performance tests:
On a private benchmark with >1k molecules, this computation only needed ~10% of the computation time.

The old computation also lead to memory-errors, when many molecules were added as training data points leading to crashes.

## Test Plan

New tests is added, for comparing old and new calculation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `010b3a0978f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.