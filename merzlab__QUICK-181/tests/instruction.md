# Issue

**Title:** Update CUDA configurations in CMake build

## Description

- Enables CUDA Toolkit 11.1 and 11.2
    - Adds SM 8.6 for Cuda > 11.0
    - Drops SM 3.0 for Cuda >= 11.0 (also updated in configure script)
    - Enables manual selection of multiple QUICK_USER_ARCH flags (e.g. "volta turing")

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1c5abcf49e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.