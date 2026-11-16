# Issue

**Title:** Improve internal job handling

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Internal jobs are jobs that are run server-side (by job runners). This PR improves them in two ways:

1. Functions that are to be run by the internal job runner do not have to have `session` or `job_progress` arguments now
2. Jobs can be repeated automatically if successfully finished (rather than using `after_function` and doing it manually)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26e69a0b934b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.