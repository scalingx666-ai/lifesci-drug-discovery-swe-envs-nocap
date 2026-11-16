# Issue

**Title:** Add weekly ASAN build

## Description

This adds an on-demand and weekly run of AddressSanitizer

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71f29b45fc86`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.