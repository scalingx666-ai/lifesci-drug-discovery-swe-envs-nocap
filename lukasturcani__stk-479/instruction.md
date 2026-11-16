# Issue

**Title:** Remove MongoDB database dump from tests

## Description

Database dump commands were not working. Dumping the databases has not provided a lot of utility. Instead of fixing, it is easier to remove.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46f70cd00089`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.