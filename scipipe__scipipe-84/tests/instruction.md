# Issue

**Title:** Add Appveyor Testing for Windows

## Description

Sadly, the tests do not currently pass. They say admitting the problem is the first step.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59b22b2a29c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.