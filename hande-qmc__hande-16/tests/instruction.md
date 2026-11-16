# Issue

**Title:** Force non-lazy allocation of particle arrays.

## Description

This now causes an error if there isn't enough RAM available when particle lists are allocated, rather than a crash in the middle of a calculation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `896d11bd055c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.