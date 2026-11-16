# Issue

**Title:** GPU FrontEnd management

## Description

Addition of a resource acting as a lock (note that the lock is only effective if the resource FRONTEND_RUNNER_GPU_LOCK is specified in the snakemake execution)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a820f664cb82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.