# Issue

**Title:** GitHub CI remove on push, add dispatch, concurrency

## Description

GitHub CI should not execute on push. Instead, trigger manually if needed.
Execute automatically only for PRs.
On new push, cancel running tests, keep only tests for latest commit running.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2714e51f523e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.