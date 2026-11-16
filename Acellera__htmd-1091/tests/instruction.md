# Issue

**Title:** Mps adaptive

## Description

Added compatibility with latest jobqueues update to use nividia_mps with Slurm in Adaptive sampling.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de4d6818c01d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.