# Issue

**Title:** Tolerate long paths for database sockets

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

On Mac/Linux, socket files have a limit on the path length. Sometimes, particularly in some testing setups, this can be too short. So if this is detected, socket files are disabled and regular TCP connections will be used.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04a522ea1e5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.