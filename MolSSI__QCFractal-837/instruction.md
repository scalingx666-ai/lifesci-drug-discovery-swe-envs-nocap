# Issue

**Title:** Commit for every returned task is processed

## Description

<!-- Thank you for your contribution! -->

## Description
Previously, nested transactions were used when a manager returns tasks. That way, there would only be one big `COMMIT` at the end when all returned tasks had been processed.

This leads to some deadlocks between services and the task queue. So now we will commit after each returned record has been processed.

Additional disk I/O should be small, and is otherwise ameliorated postgres-side by disabling synchronous commits (which I do on production servers).

## Changelog description
Commit for every returned task

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6fa19fcd57f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.