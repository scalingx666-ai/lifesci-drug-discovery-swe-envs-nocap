# Issue

**Title:** Update turbomole updater class

## Description

Updates turbomole updater (half sorts issue #227) to:

-  check the coordinate units (although fractional coordinates not implemented because complex, and unnecessary - an error is implemented if this comes up)

- coordinate section placement in file is not hardcoded.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b9173b0766f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.