# Issue

**Title:** Fix translational invariance for multipoles

## Description

The multipole moment was not completely translationally invariant. The onsite overlap matrix entries were set to the identity matrix instead of being explicitly calculated (on the order of 1e-9 Eh for the energy and 1e-8 Eh/Bohr for the gradient). This PR is based on #1473 (reuses the potential from the SCC for the gradient after the earlier convergence). Will be rebased after #1473 is merged

The effect of removing the multipole integral list neglect is within the noise between different SCF runs. 

This prepares the long-term switch to using tblite for all Hamiltonians by fully aligning the xtb and tblite SCF results.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5614e81d5cf3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.