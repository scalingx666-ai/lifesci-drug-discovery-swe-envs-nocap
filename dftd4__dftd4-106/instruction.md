# Issue

**Title:** Allow linking against custom linear algebra backend

## Description

Fixes OpenBLAS finder and allows `-Dlapack=custom -Dcustom_libraries=blis,lapack`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1065faa3c6ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.