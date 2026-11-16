# Issue

**Title:** Rework multiprocessing code + logging

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Some small reworking of multiprocessing. This moves the targets of multiprocessing to separate files, and modified the CLI code to use these. This also cleans up the logging situation there a bit.

This also adds `multiprocessing.Event`s to signal when the target of the multiprocessing is initialized. These are then used in the snowflake.

This also updates the Snowflake (and testing infrastructure) to use these events.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81a5da0a1454`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.