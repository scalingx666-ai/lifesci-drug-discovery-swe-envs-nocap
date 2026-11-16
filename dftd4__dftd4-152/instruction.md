# Issue

**Title:** Add type generic macro for deleting API objects

## Description

- dispatch object handles to their respective deconstructor using _Generic
- automatically handle pass by reference of the object handle

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1faf68231d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.