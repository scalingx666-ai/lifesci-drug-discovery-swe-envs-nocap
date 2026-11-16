# Issue

**Title:** Save all torsion values

## Description

## Description
All torsion values from the initial parameterisation are now saved, this fixes a bug where dummy values were dropped when trying to parameterise a molecule with missing coverage in the base force field. 


## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2132ccd44d76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.