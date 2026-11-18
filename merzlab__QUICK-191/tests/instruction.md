# Issue

**Title:** Fix for issue 190

## Description

I have updated the density matrix cutoff to 10-6. This should fix issue #190. Please merge when CI tests are done.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ec9d19c7cb3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.