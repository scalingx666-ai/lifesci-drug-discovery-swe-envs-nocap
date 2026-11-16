# Issue

**Title:** Improve memory usage, fix molecule bugs

## Description

This PR accomplished the following:

Bugs Fixed
• GPU Workflow: Calculation of Tanimoto distance for SpearmanR was using PCA-generated embeddings rather than Morgan Fingerprints, causing a NaN value. Now correctly using Morgan Fingerprints.
• Number of molecules is now correctly counted in GPU workflow logging when set to -1 (all molecules)

Improvements
• Memory requirements are improved by only storing input arrays for metrics when benchmarking, and when stored, they are pre-sampled 
• Pre-sampling of arrays allowed metric calculations to be streamlined

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fed947816ff1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.