# Issue

**Title:** Added option to disable angle/dihedral regeneration

## Description

Necessary, especially for TIP4P where it guesses angles with lone pairs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7879446e2415`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.