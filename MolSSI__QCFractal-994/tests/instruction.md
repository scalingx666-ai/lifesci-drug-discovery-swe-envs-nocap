# Issue

**Title:** Rework database locking to use upserts when possible

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This PR reworks some of the locking mechanics when used for molecules and specifications. Before, we used advisory locks to prevent duplicates or esoteric errors. This PR implements true upserts in postgres (ON CONFLICT DO NOTHING) when possible. For molecules and most specifications (except manybody) there is a unique constraint in the tables, making this lighter weight that advisory locks.

Performace difference is small, but possibly slower on insert in this version. However, this should prevent several kinds of deadlocks we have been seeing in the database, where several concurrent processes end up waiting for each other indefinitely. These deadlocks are caught by postgres so they do terminate, but users get a nasty error.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8432252ffd5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.