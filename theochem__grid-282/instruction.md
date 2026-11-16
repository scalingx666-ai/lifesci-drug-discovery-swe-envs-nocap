# Issue

**Title:** Fix the problem when have negative number of points (Fix #273)

## Description

When the number of points is negative, it indicates the coordinate units are Bohr instead of Angstroms, https://gaussian.com/cubegen/. Therefore, I added this to the metadata and fixed the cube generation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d597f0d67f90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.