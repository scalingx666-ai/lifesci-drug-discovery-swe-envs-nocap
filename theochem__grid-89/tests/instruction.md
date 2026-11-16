# Issue

**Title:** Fix warning in code

## Description

1. Update setup with scipy dependency to 1.14
2. Update random().as_dcm() to random().as_matrix()
3. Silence runtimewarning when construct grid

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5c2ca232060`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.