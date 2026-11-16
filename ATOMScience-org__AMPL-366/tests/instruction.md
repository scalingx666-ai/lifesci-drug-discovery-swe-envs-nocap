# Issue

**Title:** Update build ci

## Description

- Fix the docker build for arm chip.
- Change the build.yml condition to generate the desired tags for production.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d4ae2a789af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.