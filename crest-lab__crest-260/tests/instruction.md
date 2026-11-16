# Issue

**Title:** Update fortran compiler version for continuous build

## Description

The GitHub workflow now uses Intel's oneAPI version 2023.1.0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f4cd005f96d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.