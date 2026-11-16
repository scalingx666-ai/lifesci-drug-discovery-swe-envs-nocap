# Issue

**Title:** Raise exception if prune returns no conformers

## Description

Raises a more helpful exception in e.g #268 

### Questions

-  Is this behaviour intuitive? Certainly useful for debugging but are there circumstances where you'd want to call `prune` and allow an empty result?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe54c1971a22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.