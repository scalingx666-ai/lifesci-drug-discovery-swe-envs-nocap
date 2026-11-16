# Issue

**Title:** Fix Rayleigh-Ritz crash for molecules with very few internal DOFs

## Description

When the number of free internal DOFs is small (e.g. 1 for a diatomic), the iterative Rayleigh-Ritz eigensolver would try to expand its subspace beyond the full space dimension, producing a zero expansion vector. Normalizing this vector caused NaN, crashing the solver.

Return early when the subspace spans the full space (V.shape[1] >= n), not just when it exceeds maxiter.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e4626c96262`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.