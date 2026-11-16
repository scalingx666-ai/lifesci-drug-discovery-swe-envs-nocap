# Issue

**Title:** Vsite default LJ parameters

## Description

## Description
This PR updates the vsite default LJ parameters to be `sigma=1` `epsilon=0` to make sure long-range corrections work when using a custom nonbonded force in opemmm during alchemical calculations.

## Status
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f002e47b2b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.