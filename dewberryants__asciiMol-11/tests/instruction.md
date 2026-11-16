# Issue

**Title:** Character Buffer less silly

## Description

Character buffer was a cols x lines sized array containing strings, it is now a sparse list of tuples containing only the actual content. Should be a little more perfomant and a lot less silly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `106a48bf3a7e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.