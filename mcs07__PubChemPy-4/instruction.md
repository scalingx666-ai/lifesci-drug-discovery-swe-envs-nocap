# Issue

**Title:** Add backwards-compatible Python 3 support

## Description

Building on top of pull request #3 by @ekaakurniawan, these commits add Python 3 support while preserving Python 2.7 support.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5134932e09dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.