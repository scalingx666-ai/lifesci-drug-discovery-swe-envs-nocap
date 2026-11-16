# Issue

**Title:** Refactor: Introduce context...

## Description

Introduce context to hold global values in a singleton class.

Also use this to reduce boilerplate code around MetricsLogger.

Other changes include fix merge issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61147483f9f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.