# Issue

**Title:** Dev/uhf specification

## Description

### Bugfix  
Fixed an issue where charged species defined as closed-shell molecules could not be processed in EI (Electron Ionization) calculations.

### Solution  
The spin multiplicity is now determined directly based on the total number of electrons and the molecular charge.  
The number of unpaired electrons is calculated under the assumption that the molecule is in a low-spin state.

This bug was introduced in the Pull request #418 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f5933d2a80c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.