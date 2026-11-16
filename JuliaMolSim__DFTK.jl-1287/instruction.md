# Issue

**Title:** Support Laplacian-mGGA response and second derivatives of XC via Libxc

## Description

Too much code duplication for my taste and no real test yet, but it seems to run, at least.

Needs a test for derivatives of laplace-based functionals.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e62c40d424f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.