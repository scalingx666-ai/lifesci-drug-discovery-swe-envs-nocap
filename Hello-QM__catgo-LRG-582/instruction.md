# Issue

**Title:** chore: migrate release secrets to private repository

## Description

One-time administrator-triggered workflow that copies existing Actions secrets directly into the private catgo-dev repository. Secret values are never logged or downloaded. The workflow will be removed immediately after successful migration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61f93d06ba2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.