# Issue

**Title:** Disable chunking for stresses

## Description

This makes stresses roughly twice as slow and allocate twice as much, but should reduce the peak memory usage by a lot.

This is only a partial fix for

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed9d38ce9221`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.