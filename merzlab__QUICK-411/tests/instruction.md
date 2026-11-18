# Issue

**Title:** HIP and MPI+HIP Updates Part 2

## Description

This PR backports data structure initialization fixes in PR #361 for the single GPU codepaths to the MPI+GPU codepaths.  Moreover, this PR unifies portions of the GPU and MPI+GPU initialization code to simplify future maintainence.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49f2418ac3a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.