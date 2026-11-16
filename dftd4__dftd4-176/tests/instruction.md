# Issue

**Title:** Export API routines for MSVC compiler

## Description

* Exports must be explictly declared for the MSVC compiler. This commit adds DLLEXPORT attributes to the subroutines needed for the api and app to compile



This still the same pull request as  Had to remake due to clunky choice of branching

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ff1dc36a3a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.