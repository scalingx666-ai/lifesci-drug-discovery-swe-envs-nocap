# Issue

**Title:** Fix IRC converging after 0 steps with ASE >= 3.23

## Description

ASE >= 3.23 checks converged() before the first step() call. Since IRC starts at a transition state where forces are ~0, this caused immediate convergence. Return False from converged() before the first IRC displacement kick has occurred.

Fixes zadorlab/sella#71

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e4626c96262`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.