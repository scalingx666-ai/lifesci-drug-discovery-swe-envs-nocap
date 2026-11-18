# Issue

**Title:** Re-enable automatic deployment of nightly documentation

## Description

This was lost in the migration to Github action (#394)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2993d8bef36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.