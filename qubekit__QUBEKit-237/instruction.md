# Issue

**Title:** [WIP] Typing and testing added to virtual_sites.py and lennard_jones.py

## Description

## Description
Added typing to virtual_sites.py and lennard_jones.py
Added various tests to a new virtual_sites.py test file. 

## Todos
  - [ ] Need to add further tests to virtual sites, particularly integration testing and testing of `fit()` method.

## Questions
- [ ] Should virtual_sites.py be written differently? Particularly wrt to passing atom_index so regularly. For example, would it be better for the sample points and atom coords to be passed as arguments?

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac032b3486d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.