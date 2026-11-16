# Issue

**Title:** Update 1e_mints-helper.ipynb

## Description

Clarify info about how to access ERIs

## Description
Fix little problem explaining ERI format for Psi4, and explain how the NumPy view is different.  Also, provide an explanation about why we might want to estimate memory requirements by multiplying ERI size by 1.5

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b40c410e404`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.