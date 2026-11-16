# Issue

**Title:** Moved all charge extraction and symmetrisation out of LJ. Removed unn…

## Description

…ecessary duplication of mol vars.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4b4f02743a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.