# Issue

**Title:** Exits working directory if wrapped function throws an exception.

## Description

If a function wrapped with `@utils.work_in` or `@utils.work_in_tmp_dir` throws an exception that is later caught, the working directory will be in the wrong location.

Note: `@utils.work_in` may have an unintended side-effect (unaffected by this PR). If an empty directory is passed to `@utils.work_in`, and nothing is produced in that directory, the directory will be deleted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5166fc1c7aa4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.