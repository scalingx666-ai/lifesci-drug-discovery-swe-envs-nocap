# Issue

**Title:** Add get_numerical_hessian_api into public API

## Description

get_numerical_hessian_api was not in the public API, which resulted in a link error of dftd4 with up-to-date versions of gfortran.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ceaea840837`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.