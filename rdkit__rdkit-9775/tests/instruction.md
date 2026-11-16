# Issue

**Title:** Consolidate duplicated Deadline handling in conformer generator

## Description

PR 3 for #9772

This doesn't actually cut down on the diff, but removes a bunch of repeats and will be useful for more downstream consolidation.

Designed by me, implemented by Claude Opus 5.5

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8196a07b5c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.