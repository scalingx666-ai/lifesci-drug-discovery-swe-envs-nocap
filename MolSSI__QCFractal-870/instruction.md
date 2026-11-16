# Issue

**Title:** Small task queue fix & migration code location

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Small fix for inconsistent index definition on the task queue table (missing the `WHERE available = true`).
Also moves code for some old migrations.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5162bc994ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.