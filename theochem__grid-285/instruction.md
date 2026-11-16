# Issue

**Title:** Enable website building check when making a pull request

## Description

Also updated the GitHub Actions version for other workflows.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `607a6c34dc55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.