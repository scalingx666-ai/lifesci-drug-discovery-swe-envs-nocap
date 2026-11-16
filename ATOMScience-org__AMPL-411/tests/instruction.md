# Issue

**Title:** Fix tests in GitHub CI

## Description

Some of the test are failing after skipping moe_required tests in the GitHub CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `869082ba142d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.