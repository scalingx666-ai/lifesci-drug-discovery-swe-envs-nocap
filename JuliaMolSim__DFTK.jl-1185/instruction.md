# Issue

**Title:** Increase GPU robustness of LOBPCG

## Description

Inversion and Cholesky decomposition of ill-conditioned matrices on the GPU (both AMD and NVIDIA) sometime yield NaN elements. This happens silently, but gets caught by the various `@assert !any(isnan, Array)` checks.

This rarely happens, but likelihood seems to increase when pushing very tight SCF convergence thresholds.

This PR introduces a fall-back to the more robust CPU routines. Impact on performance is negligible (rare event), and stability is greatly improved.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99ac78a7e73a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.