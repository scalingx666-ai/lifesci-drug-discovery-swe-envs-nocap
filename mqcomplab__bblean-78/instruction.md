# Issue

**Title:** Fix multiround bug and add option to refine between midsection rounds

## Description

Fix bug in `bb multiround` that returned bad indices when refinining. Update CLI for better ease of use and add option to refine after midsection rounds (non-default).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca897d7df9f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.