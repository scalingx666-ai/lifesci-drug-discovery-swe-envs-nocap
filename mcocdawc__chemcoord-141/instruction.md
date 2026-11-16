# Issue

**Title:** allow more number types for scaling

## Description

This fixes a bug where `zmat * 2` does not work, because only floats where allowed for scaling.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea947de69368`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.