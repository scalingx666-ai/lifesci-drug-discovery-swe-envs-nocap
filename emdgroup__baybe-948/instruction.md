# Issue

**Title:** Update pytest ignores

## Description

* Adds the latest pandas 4 deprecation warning (error is suppressed instead of fixed due to pending narwhals migration)
* Drops some obsolete ignores

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42a161021c92`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.