# Issue

**Title:** Completion base support

## Description

Completion works on TAB.
The following tokens are took int account:
- user-defined variables
- user-defined functions
- keywords

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fdf1a3db7fcc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.