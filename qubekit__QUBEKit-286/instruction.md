# Issue

**Title:** QFroce Urey-Bradley terms

## Description

## Description
This PR adds the ability to fit Urey-Bradley terms using QForce. We also add a special pdb writing method which adds extra connections between UB potential atoms allowing the use of the force fields in normal openmm scripts, these pdbs are automatically output when we detect UB terms in the molecule. 


## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbdd24f30628`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.