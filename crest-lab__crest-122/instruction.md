# Issue

**Title:** Fix for forrtl: warning in #121

## Description

The internal write on these two occasions was somehow messed up.
Replacement code should fix it, despite being ugly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `318c3cc54e70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.