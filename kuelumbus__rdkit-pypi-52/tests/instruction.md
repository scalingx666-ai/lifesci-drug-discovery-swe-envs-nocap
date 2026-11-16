# Issue

**Title:** Include contrib directory

## Description

Build wheels that include the contrib folder. The wheel size will grows significantly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ef66cfdb4ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.