# Issue

**Title:** Fix for GCC 14

## Description

This patch removes uninitialised but used stmp that leads to bugs with novel GCC's. All cmake tests for xtb were passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43a0e4e5b5d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.