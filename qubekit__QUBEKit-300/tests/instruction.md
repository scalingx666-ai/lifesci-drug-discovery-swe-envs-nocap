# Issue

**Title:** Psi4 minimum version check

## Description

## Description
This PR introduces a minimum version check for psi4 during the MBIS stage to ensure MBIS is available. 

We have also changed the default pre-optimisation method to use xtb as this is more reliable than the qcengine rdkit/uff interface. 

The CI is also updated to run MBIS tests on the newest version of psi4 1.5.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [ ] turn on MBIS tests 


## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80df16d355a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.