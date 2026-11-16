# Issue

**Title:** Broken by Last PR

## Description

On the last PR, I changed the POLYCRYS function and forgot to change one file that calls it. This fixes that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dca8afc2e099`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.