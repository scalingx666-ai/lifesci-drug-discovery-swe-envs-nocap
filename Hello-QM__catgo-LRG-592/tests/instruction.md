# Issue

**Title:** ci: disable automatic PR checks

## Description

Stop automatically running Docker, lint, test and Python verification workflows for pull requests. Restrict Python verification on push to main so PR branch pushes do not start the same checks.

Existing main-branch, release and manual triggers remain available. Workflow jobs are unchanged.

Validation: parsed every modified YAML file and checked that only PR triggers and the Python push branch filter changed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd6291b8d4ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.