# Issue

**Title:** Bugfixes for CUDA >= v13.x

## Description

This PR contains trivial code changes to fix builds with CUDA >= v13.x due to removal of deprecated API features (specifically, `clockRate` from the `cudaDeviceProp` struct).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2759f6a9d7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.