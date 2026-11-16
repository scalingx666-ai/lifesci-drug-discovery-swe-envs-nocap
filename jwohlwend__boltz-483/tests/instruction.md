# Issue

**Title:** Fix: update filter_inputs_affinity to only filter records if override=False

## Description

Fixes a bug that caused affinity predictions to be skipped even if `--override` was set

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb221d396506`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.