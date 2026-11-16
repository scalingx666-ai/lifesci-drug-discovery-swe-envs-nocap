# Issue

**Title:** Hash browser session keys at rest in the database

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Raw (unhashed) session keys, if leaked, could be used to impersonate a users. This hashes those keys, preventing use by a third party should they ever be disclosed.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b963bfe89170`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.