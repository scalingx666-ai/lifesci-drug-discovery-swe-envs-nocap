# Issue

**Title:** Update the dftd4 version to fix inconsistencies with tblite

## Description

Update to dftd4 4.2.0 with the smooth periodic cutoffs used in the current tblite main branch. Should fix the current build issues of xtb.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ebfc7bd98da7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.