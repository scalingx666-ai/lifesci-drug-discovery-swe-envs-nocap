# Issue

**Title:** migrate FormatStringBuffer to FormatStringBuilder

## Description

- replace StringBuffer with StringBuilder for improved performance
- update dependencies and related test classes accordingly
- simplified code and removed code smells

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0750f7b09a8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.