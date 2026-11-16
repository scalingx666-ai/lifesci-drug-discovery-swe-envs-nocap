# Issue

**Title:** Replace Ubuntu 20.04 with 22.04

## Description

Ubuntu 20.04 runners are discontinued and GCC8 is not on 22.04 anymore.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2596f98ebc46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.