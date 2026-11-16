# Issue

**Title:** dfbtplus: unstable-2024-08-23 -> unstable-2025-04-11

## Description

Update of DFTB+ to more recent version. Splits out python packaging and makes MPI and GPU support optional.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4d92ef6a751`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.