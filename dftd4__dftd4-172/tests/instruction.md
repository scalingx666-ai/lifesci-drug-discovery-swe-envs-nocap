# Issue

**Title:** build(cmake): enable language C to use MKL as BLAS

## Description

FindBLAS requires C or CXX to be enabled in order to use MKL.
https://cmake.org/cmake/help/v3.14/module/FindBLAS.html#result-variables

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e4ea97f90b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.