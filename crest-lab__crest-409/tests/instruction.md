# Issue

**Title:** 3.0.2 maintenance

## Description

- Fix generic script/subprocess handing for parallel code parts in calculator setup
- Fix atom freezing in combination with SHAKE

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09b1ba93b46c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.