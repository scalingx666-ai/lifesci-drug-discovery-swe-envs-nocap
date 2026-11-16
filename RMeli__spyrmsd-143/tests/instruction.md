# Issue

**Title:** Optionally return best graph isomorphism

## Description

## Description
I found it useful to obtain the atom mapping corresponding to the lowest RMSD. This is something that RDKit's `CalcRMS` function lacks. For that I added a new function, rather than modifying `symmrmsd`, to avoid conflicts with existing implementations.

## Changes
- Added function `symmrmsd_and_isomorphism `, which is identical to `symmrmsd` but also returns the best isomorphism for each minimum RMSD
- Modified `_rmsd_isomorphic_core` to return the best isomorphism
- Adapted return value of `_rmsd_isomorphic_core` for function `symmrmsd`
- Changed type hints for function `symmrmsd`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58e8b525584d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.