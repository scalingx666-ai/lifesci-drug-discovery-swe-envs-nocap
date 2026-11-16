# Issue

**Title:** Docker prep

## Description

- Fixed the lightning version in the CI job by removing 'uv run...'.
- Widened the version range in cpu requirements.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `921885c6daf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.