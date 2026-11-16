# Issue

**Title:** Fix gradient for ATM contribution

## Description

Gradient contributions in periodic ATM were not correctly rescaled.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97ed71ef7f02`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.