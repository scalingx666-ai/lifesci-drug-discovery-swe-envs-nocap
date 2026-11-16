# Issue

**Title:** Build LEBEDEV_DEGREES from LEBEDEV_NPOINTS

## Description

This is a very minor change. Unless there is a specific reason to keep both dictionaries, I think it is less error-prone to build one from the other. Feel free to let me know what you think.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e32931c4d79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.