# Issue

**Title:** LR scheduler mode=max -> mode=min

## Description

## Description
The scheduler should be using plateauing based on decreasing losses, not increasing -- correct?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d57bd1598c3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.