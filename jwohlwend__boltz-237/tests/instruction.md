# Issue

**Title:** raise exception instead of dict in OOM handler

## Description

The code attempted to 'raise' a dictionary when the error was not "out of memory,"
causing TypeError. This commit just ensures the original exception is re-raised properly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `330cb969a8f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.