# Issue

**Title:** BIO-3: fix multi-gpu mfsdp tests

## Description

turn off clip grad norm until we can fix BIO-3

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7dd1659f2103`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.