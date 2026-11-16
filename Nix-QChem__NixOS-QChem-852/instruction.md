# Issue

**Title:** et: add reduced mass patch

## Description

eT does not show the reduced masses of normal modes, but outputs normalized displacement vectors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2f7ae72f326`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.