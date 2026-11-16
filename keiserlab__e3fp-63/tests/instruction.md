# Issue

**Title:** Use smart_open package

## Description

This PR moves away from using the (hackish) `smart_open` function in `python_utilities` to the well-tested `smart_open.open` function in the `smart_open` package.

 and #47

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `442f5110725a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.