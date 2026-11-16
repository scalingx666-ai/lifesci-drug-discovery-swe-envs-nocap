# Issue

**Title:** Report multithreaded test assertions after joining workers

## Description

Mostly harmless TSAN catch

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15e2be3f352b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.