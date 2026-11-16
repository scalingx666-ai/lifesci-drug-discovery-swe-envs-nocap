# Issue

**Title:** Recovers separate output dirs for different forcefields

## Description

Also:
- changes in printing functions
- fixing parameterize tutorial
- minor fixes in long tests

This won't pass tests for now, as I haven't changed the data. @raimis, can you pre-approve what's done, and then I change data to match the changes?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31cd7fe82501`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.