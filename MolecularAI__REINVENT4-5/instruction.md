# Issue

**Title:** Added iwdescr

## Description

Implementation of iwdescr from the Lilly https://github.com/EliLillyCo/LillyMol provide 259 descriptors as scoring component.  Any descriptor can be chosen and integrated into the total scoring function just like any other component.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3572da1fa1b9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.