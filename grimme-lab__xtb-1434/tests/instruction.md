# Issue

**Title:** Fix file descriptor leak

## Description

`releaseOutput_api` had a logic bug, where it would only attempt to free stdout, stderr, or an unset file descriptor, where the intended behavior was to free any other file descriptor.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a45f05d39726`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.