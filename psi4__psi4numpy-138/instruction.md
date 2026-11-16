# Issue

**Title:** Fixing several errors in the EOM-CCSD code in Psi4NumPy.

## Description

## Description
The EOM-CCSD code has a few errors that yield poor convergence of the Davidson algorithm.  This PR corrects those and improves the convergence from 70 iterations to 12-14 even with an order of magnitude tighter criterion in the excitation energies.

* **Changes**
  - [X] Correct initial unit-vector guesses to correspond to roughly HOMO-LUMO singles rather than 1s core to LUMO singles.
  - [X] Correct a mathematical error in the preconditioner in which only a single element of the orbital energy denominators was used rather than the entire vector.
  - [X] Correct the conversion factor from Hartrees to eV. (An incorrect value of 22.211 was hardcoded; I've converted this to use the `qcelemental` entry.)
  - [x] Adjust the size of the guess spaces to force the algorithm to collapse when the maximum allowed dimension is reached.  This is only to ensure that the relevant part of the code is tested and demonstrated.

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f2f86762f6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.