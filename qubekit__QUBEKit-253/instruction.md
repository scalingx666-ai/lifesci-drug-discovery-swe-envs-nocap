# Issue

**Title:** Torsion ForceBalance update

## Description

## Description
This PR finishes the ForceBalance interface with some sensible default optimisation settings.
The L1 regularisation method is used with a 0.1 additive penalty.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [X] Implement the ForceBalance interface.
  - [X] Test on molecules with multiple rotatable bonds.

## Status
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `806abd6bebcc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.