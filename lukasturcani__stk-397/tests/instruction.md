# Issue

**Title:** Use a flake8 config file

## Description

Use a config file for flake8, instead of specifying options in the
workflow file. This ensures that flake8 uses the same options regardless
of if it is run manually or in CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7358ba91b32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.