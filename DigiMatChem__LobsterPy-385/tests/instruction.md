# Issue

**Title:** Fix bloated src distribution on pypi

## Description

# Changes

1. Exclude wanted test, examples, paper and docs directories from src distribution on pypi

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5b446d6f991`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.