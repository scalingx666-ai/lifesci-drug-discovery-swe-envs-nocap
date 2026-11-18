# Issue

**Title:** Added a check before saving highlighted atoms

## Description

An issue can occur where the atoms highlighted of on atoms are carrying over to the next molecule.
This fix, fixed the issue. However, the issue should not occur even without the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77ee4646e8ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.