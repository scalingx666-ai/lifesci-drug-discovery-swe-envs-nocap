# Issue

**Title:** Sites angle symmetry update

## Description

## Description
This PR adds a flag `freeze_site_angles` which controls if the angle between 2 virtual sites for the 2 sites 2 bonds case is to be optimised or not. For example 2 sites on alcohol currently have a fixed angle of 90 degrees with this flag set to `True` when set to `False` this optimises to around 111 degrees.  

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [X] add tests for both cases

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b02dcd2eb967`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.