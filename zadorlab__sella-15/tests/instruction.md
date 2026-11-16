# Issue

**Title:** Make IRC forward/reverse direction choice deterministic

## Description

Define v0ts to be the direction where the first nonzero element is positive. This should prevent non-deterministic direction choice of this eigenvector which makes it difficult to run independent forward and reverse IRCs (as in some cases the reverse and forward IRCs pick different v0ts's causing them to be the same IRC branch).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55c40ab45e24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.