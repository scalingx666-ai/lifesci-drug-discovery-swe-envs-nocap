# Issue

**Title:** Ignore Benchmarking Env Var

## Description

The benchmarking submodule currently maintains a single environment variable for the CI to set the S3-Bucket name and was unknown to the Setting validation class. To prevent a runtime error, env variables from the benchmarking submodule are now ignored and maintained by the module itself.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ddaf7caa13af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.