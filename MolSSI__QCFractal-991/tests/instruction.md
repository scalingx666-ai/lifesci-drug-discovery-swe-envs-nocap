# Issue

**Title:** Fix /me endpoint and add tests

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Modifying the user through the /me endpoint was broken due to a missing parameter to the socket function. This fixes that, and adds tests for the /me endpoints.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d82c54668735`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.