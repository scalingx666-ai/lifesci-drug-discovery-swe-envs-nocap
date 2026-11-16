# Issue

**Title:** Fix optimization when davidson fails

## Description

In rare cases when davidson fails, solver_sspevx was called. Unfortunately, it did not update fail variable, so, if it even was successful, fail variable still was true and therefore optimization was failing.

This patch fixes this issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88182d28a757`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.