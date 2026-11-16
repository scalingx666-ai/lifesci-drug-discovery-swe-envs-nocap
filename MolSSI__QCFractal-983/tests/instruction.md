# Issue

**Title:** no more geometric.qcf_neb.prepare() for the server

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
1. The NEB service no longer calls `geometric.qcf_neb.prepare()`, since  This way, the compute nodes carry out the tasks from the `prepare()` function. 
2. `geometric.qcf_neb.arrange()` accepts a nested list instead of a Molecule object. 

The neb tests in `test_full_neb.py` are passing with the  on the geomeTRIC side. 

## Status
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c332ec0ee980`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.