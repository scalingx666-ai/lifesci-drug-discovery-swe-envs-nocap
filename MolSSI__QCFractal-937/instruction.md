# Issue

**Title:** Add query for active managers

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This adds a query + client function that queries active managers for particular tags and programs. This can be used to determine if a prospective calculation has a manager that could possibly pick it up.

This requires a small db migration (changing the manager programs column from JSON to JSONB)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fe9491802c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.