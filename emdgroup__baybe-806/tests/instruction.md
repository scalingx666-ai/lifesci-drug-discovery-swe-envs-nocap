# Issue

**Title:** Handle hypothesis float overflow

## Description

Fixes a numerical problem that surfaced due to newer hypothesis version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d7eb823769c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.