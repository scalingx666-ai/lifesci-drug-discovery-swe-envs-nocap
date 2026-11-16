# Issue

**Title:** Update `setup-miniconda` to v2

## Description

`add-path` and `set-env` commands are deprecated and will be disabled on November 16th. More information see: https://github.blog/changelog/2020-10-01-github-actions-deprecating-set-env-and-add-path-commands/

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73d506dc5ec7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.