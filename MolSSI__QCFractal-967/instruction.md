# Issue

**Title:** Change how child records are stored (don't use PrivateAttr)

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This changes the way child records are stored internally inside records. Before, they were stored as PrivateAttr, which means they were never serialized if you used pydantic's `dict()` function.

However, for saving/transferring/ingesting complete records, we want those child records in place. So this PR makes those child records regular fields.

However, we DON'T want those child records when writing to cache files (where they are handled differently). So a separate function was added for that.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5735f6503e98`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.