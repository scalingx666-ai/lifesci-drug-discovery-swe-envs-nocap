# Issue

**Title:** Harden and improve tests

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This PR aims to help stabilize tests and reduce spurious errors. This also makes the tests safer to run in parallel by removing hard-coded ports and paths and stuff.

Also fixes a race condition where a temporary directory could be deleted before a snowflake was properly shutdown.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e539d5a5c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.