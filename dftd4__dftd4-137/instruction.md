# Issue

**Title:** Refactor Python API

## Description

- make error handling cleaner by using functools
- error out if both a method and parameters are provided to damping function constructor

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `982bb90fc0b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.