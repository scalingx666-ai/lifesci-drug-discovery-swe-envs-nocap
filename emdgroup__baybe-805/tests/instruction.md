# Issue

**Title:** Lock docs pipeline

## Description

Enforce lockfile consistency in the docs tox pipeline by passing `--locked` to `uv run`, preventing silent use of stale dependency pins.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50432ad9860b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.