# Issue

**Title:** Add TPR files with format version 2023

## Description

Removes warning the warning "file version is from the future" when reading TPR files produced by GROMACS version 2023.
Also, added test files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `481b5befa2fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.