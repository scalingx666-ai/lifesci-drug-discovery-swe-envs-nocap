# Issue

**Title:** Makefile updates

## Description

- Updates a bug with the GPU_ARG when running GPU with docker
- Loosens up dependency for tensorflow for `arm64` builds
- Relates to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d4ae2a789af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.