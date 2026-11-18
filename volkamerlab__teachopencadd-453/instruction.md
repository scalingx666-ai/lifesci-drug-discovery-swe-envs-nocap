# Issue

**Title:** CI updates

## Description

- Trigger Docs CI on all branches: This allows the formatting bot to commit to the PR branch
- Workflow dispatcher: CI actions can be manually started this way
- T037 formatting

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ffe190b334e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.