# Issue

**Title:** Don't specialize connectedcomponents for subgraphs

## Description

The generic fallback gives the correct answer, but the specialization does not.

I made this PR in two commits; the first is the failing test, the second is a fix, to make it easy to replicate. Feel free to squash this when you merge.

I am not sure whether others should also have such specializations removed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ffff50e23841`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.