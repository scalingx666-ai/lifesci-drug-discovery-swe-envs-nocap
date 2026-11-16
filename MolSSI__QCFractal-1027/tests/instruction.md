# Issue

**Title:** Default to verifying SSL certificates for compute managers

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

In compute manager configuration, the default for verifying SSL certificates of servers was "None". This changes it to be always bool, and to default to be True.

Should have very little effect on current users, but is a safer default (now that getting certificates is very easy).

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71c3c30fdf9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.