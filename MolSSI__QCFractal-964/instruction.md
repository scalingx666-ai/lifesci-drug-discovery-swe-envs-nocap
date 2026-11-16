# Issue

**Title:** Make flask storage socket less global

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

The global `storage_socket` in flask app was not safe for use when there are multiple flask apps (sometimes happens with snowflakes if using threads). This makes the storage socket object more app-aware and context-aware.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0fbf97a8f475`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.