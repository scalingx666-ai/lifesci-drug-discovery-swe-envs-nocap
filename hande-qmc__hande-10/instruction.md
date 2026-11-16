# Issue

**Title:** Use flush statement in preference to flush subroutine

## Description

The former is preferred from F2003 onwards and the latter is
a (commonly implemented) extension which breaks some compilers (e.g.
gfortran 7.1) if a strict standard flag is used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea2d6bbaa910`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.