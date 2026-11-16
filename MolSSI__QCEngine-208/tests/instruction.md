# Issue

**Title:** Fix for NWChem Gradients with >1 MPI Rank

## Description

## Description
Bug fix: I did not test with >1 MPI rank for NWChem gradients, and found I needed to have all threads read from the database.

Also changed atom_map to False, as suggested in #205 

## Changelog description
[I would call this under the same description as the previous NWC gradients PR]

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95261637d57f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.