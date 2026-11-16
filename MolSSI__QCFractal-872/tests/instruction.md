# Issue

**Title:** Simplify & fix sorting of task queue for services

## Description

## Description

This simplifies the logic where service dependencies inherit the parent service's create_on as a sort date. Now it doesn't involve that pretty gnarly query in exchange for not handling very rare edge cases where a dependency is part of multiple services.

Also fixes a very dumb mistake - the default value of the `sort_date` in the task queue should be a function, not a value.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4bd800c9e09e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.