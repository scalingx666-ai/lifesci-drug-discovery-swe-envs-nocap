# Issue

**Title:** Restrict coverage to core library

## Description

Proper coverage metrics. Exclude tests, subprojects, etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6e09df39b9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.