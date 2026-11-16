# Issue

**Title:** sigma factor not carried through to derivatives

## Description

There is a factor of a half from the pair of equivalent lines in Hugenholtz self-energy diagram in the sigma terms. E occurs in the denominator so derivative with respect to E will be of form -E^-2, so the overall factor will be - half. Defined constant definition for au to eV in one place rather than scattered throughout code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68cd9fb8738e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.