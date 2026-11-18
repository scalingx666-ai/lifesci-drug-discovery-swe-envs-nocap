# Issue

**Title:** Add CMake build support for LLVM Flang (Fortran)

## Description

This PR backports support for CMake builds with LLVM Flang (Fortran) from upstream AmberTools (see MR#1876).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a56153ceb6f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.