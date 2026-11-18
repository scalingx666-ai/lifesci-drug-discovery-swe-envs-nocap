# Issue

**Title:** Fix doc

## Description

# Changes

1. Degrade ipython that still supports 3.9
2. Update doc build test to run on python 3.9 instead to 3.10

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35e0408ac7c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.