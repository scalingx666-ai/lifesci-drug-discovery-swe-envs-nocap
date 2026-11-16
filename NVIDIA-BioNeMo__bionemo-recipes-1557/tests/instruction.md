# Issue

**Title:** remove unused configs

## Description

Removing unused config files, and renaming the llama one to be more specific (will update it with fp8 stuff in a follow-up MR).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `191c7dc23a62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.