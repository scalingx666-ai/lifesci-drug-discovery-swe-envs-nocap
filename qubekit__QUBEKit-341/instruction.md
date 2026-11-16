# Issue

**Title:** fix plugin sites

## Description

## Description
This PR fixes the local vsite plugin by making it incompatible with the standard vsite handler from openff, we also ensure sites are added to openmm systems and topology in the same order as the reference particles so they can be associated with the correct molecule.  

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60f34c12a6f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.