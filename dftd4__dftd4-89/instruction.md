# Issue

**Title:** Allow to link against mkl_rt library

## Description

- Python extension module must be linked against `mkl_rt` to work correctly with MKL

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eaefd3334fc4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.