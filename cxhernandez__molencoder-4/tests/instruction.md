# Issue

**Title:** Use Original Architecture

## Description

Get rid of the fancy BatchNorm and DropOut layers, until we can get a decent model with the original architecture.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0bde236aacf0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.