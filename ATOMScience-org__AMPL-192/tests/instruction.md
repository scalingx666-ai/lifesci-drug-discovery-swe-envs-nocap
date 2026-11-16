# Issue

**Title:** updated tests to work with the new check_task_columns()

## Description

check_task_columns() was changed from a FileDataset method to a module-level function. Updated the tests to call model_dataset.check_task_columns instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7808e6b10abd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.