# Issue

**Title:** avoid initializing input transform

## Description

working on #694 
Enabled re-usage of properties, which are generated in the actual surrogate class instances.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a36c0d2a3828`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.