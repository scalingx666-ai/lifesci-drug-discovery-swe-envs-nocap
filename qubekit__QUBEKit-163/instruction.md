# Issue

**Title:** Changed charge data extraction to occur immediately after calculation…

## Description

…. This prevents conflicts in the mutation of charge data at different times.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0edf4d6aff1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.