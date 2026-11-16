# Issue

**Title:** disable env caching

## Description

## Summary

Disable full micromamba environment caching for the `pt-features`, `gauxc`, and
`ftorch` example jobs. Package download caching remains enabled.

## Motivation

The `pt-features` job intermittently terminated with exit code 132 (`SIGILL`)
when restoring a cached micromamba environment. Running the same job with a
freshly created environment succeeded.

The environment cache key includes the Conda platform and environment file
contents, but not CPU capabilities such as Conda's `__archspec` or the exact
resolved package set. A native environment created on one hosted runner may
therefore be restored on another runner with different CPU characteristics or
retain otherwise stale native state.

The remaining example jobs also compile and execute native code, so the same
policy is applied consistently to all three jobs.

## Changes

- Set `cache-environment: false` for `pt-features`, `gauxc`, and `ftorch`.
- Keep `cache-downloads: true` to retain package download reuse.
- Document why full environment caching is disabled.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b483362b8081`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.