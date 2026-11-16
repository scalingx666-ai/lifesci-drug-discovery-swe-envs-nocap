# Issue

**Title:** Fixed race condition in ceh numgrad

## Description

Numerical gradient using any omp parallelization leads to completely different results due to a race condition due to the shared `mol%xyz`. This is now fixed using a private copy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d484ace401ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.