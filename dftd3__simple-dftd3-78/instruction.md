# Issue

**Title:** Fixes invalid escape sequences

## Description

Uses raw strings to supress the `SyntaxWarning` thrown by python3.12.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbaae108c080`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.