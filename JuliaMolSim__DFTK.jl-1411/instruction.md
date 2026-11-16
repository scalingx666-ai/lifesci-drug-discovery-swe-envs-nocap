# Issue

**Title:** Clearer error for VoxelAverage without FastGaussQuadrature

## Description

Without FastGaussQuadrature loaded, VoxelAverage failed with the misleading 
"VoxelAverage has no pointwise Fourier representation"

It now says 
"VoxelAverage is currently not available. A required package (FastGaussQuadrature) is not yet loaded."
like save_scfres/load_scfres do for their packages.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b3fd1c49218`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.