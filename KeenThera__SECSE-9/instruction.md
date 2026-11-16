# Issue

**Title:** add custom filter

## Description

The user can modify the file open_filter.py in  in SECSE/secse/utilities. New function can be added into the open_filter.py. The input parameter of the function is an rdkit mol object,  and the return value is a boolean. If the molecule is needed, return true;  if it is not needed, return false.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38226666f0d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.