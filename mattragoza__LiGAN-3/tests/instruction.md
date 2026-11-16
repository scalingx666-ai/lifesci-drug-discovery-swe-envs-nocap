# Issue

**Title:** Enforce valence constraints

## Description

Prioritize removing hypervalent bonds over other undesirable bonds.  Use rdkit limit for valence even when making obmol.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4947338c22b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.