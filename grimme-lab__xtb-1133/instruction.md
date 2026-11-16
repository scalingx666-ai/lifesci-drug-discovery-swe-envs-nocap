# Issue

**Title:** Better support for finding custom lapack implementaion

## Description

Find and also validate usability of lapack and blas libraries.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee064757917f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.