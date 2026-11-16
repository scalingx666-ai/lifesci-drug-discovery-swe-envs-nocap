# Issue

**Title:** Remove signal termination for windows compatibility

## Description

signal.SIGALRM is not present on Windows, so switch to a decorator using multiprocessing instead. **Should** improve Windows compatibility

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6b5e011e2e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.