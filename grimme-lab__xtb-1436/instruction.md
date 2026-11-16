# Issue

**Title:** Ensure a restart file is written after convergence failure

## Description

Just adds writing/dumping of restart files to before the calculation termination that would occur if the initial SCC failed to converged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a45f05d39726`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.