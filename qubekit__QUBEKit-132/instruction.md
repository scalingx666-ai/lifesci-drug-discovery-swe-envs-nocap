# Issue

**Title:** Fix mod sem method for linear bonds; clean up mod sem a little (bette…

## Description

…r naming, docstrings, etc); begin breaking up Charges to allow for changes to mono esp calculation; remove is_protein arg and replace with internal attribute.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eac6156c076b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.