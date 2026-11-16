# Issue

**Title:** IRC initial release

## Description

Implemented SG2 schema for IRC. Still has problems with hessian update, so effectively first-order for now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `264b1e891628`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.