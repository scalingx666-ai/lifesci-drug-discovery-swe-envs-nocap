# Issue

**Title:** Fixing aISS distance constrain fix

## Description

Fixed a bug that caused crashes during the aISS procedure when distances, angles, or dihedral angles were constrained.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2f74e186c8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.