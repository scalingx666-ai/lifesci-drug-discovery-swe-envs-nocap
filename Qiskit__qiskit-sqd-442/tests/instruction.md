# Issue

**Title:** Backport Windows support and prepare 0.14.1 release

## Description

Backport of #441, with a few tweaks for stable backport.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b35c9f9c1c7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.