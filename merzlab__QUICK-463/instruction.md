# Issue

**Title:** Ambertools 2026 CMake and Test Utility Updates

## Description

This PR backports CMake build and test utility updates from AmberTools 2026 into the QUICK codebase.

Note that MPI and CUDA CMake divergences are maintained for QUICK-specific support.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `750373e13573`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.