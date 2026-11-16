# Issue

**Title:** Improve observer conditions

## Description

- Separate the trigger and definition of the observer.
- Disconnect it when unload.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f77f16d9ab21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.