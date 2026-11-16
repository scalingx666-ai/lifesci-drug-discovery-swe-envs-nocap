# Issue

**Title:** Pass AWS_DEFAULT_REGION env variable to container

## Description

This fix supports the ability of Docker executors to access S3 buckets regardless of region.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbdca3130f8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.