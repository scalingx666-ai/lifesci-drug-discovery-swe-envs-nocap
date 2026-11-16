# Issue

**Title:** ci(build_bindings.yml): prevent concurrent runs

## Description

Already defined in `build_cmake.yml`, to equally prevent concurrent instances
as defined by this workflow is deemed helpful.

## Summary by Sourcery

CI:
- Configure concurrency settings in build_bindings.yml to group runs by workflow and ref and cancel in-progress runs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e94434fa75c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.