# Issue

**Title:** cleaning up MP2_Hessian.py

## Description

## Description
Genera and very basic clean up of MP2_Hessian.py script

## What are your new additions? Please provide a brief list.
* **Changes**
  - [x] Renamed anonymous custom basis set to a more easily understood "STO-3G_CFOUR"
  - [x] Correct "H_psi4" to "H_cfour"
  - [x] Correct "RHF-HESSIAN-TEST" to "MP2-HESSIAN-TEST"

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81ad8488947d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.