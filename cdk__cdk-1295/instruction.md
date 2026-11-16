# Issue

**Title:** Watch out for NaN when the offset of double bonds is computed.

## Description

Hard to write a test case but basically we had some NaN creeping in so we account of that

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4639c7677549`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.