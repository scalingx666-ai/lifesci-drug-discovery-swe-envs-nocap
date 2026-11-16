# Issue

**Title:** Add test for MPI-3

## Description

This adds a configure-time check for availability of MPI-3 features and adds a `HAS_MPI3` preprocessor definition. 
Modern versions of CMake (>= 3.10) are capable of determining `MPI_<LANG>_VERSION` on their own, but I think that's asking for a too new version of CMake. So, I basically duplicated the version detection code that @jsspencer pointed to. If you want to use MPI-3, you can protect the code with preprocessor `if`-s checking for `HAS_MPI3`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `671f87b13415`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.