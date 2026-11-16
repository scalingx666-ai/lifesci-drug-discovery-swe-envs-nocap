# Issue

**Title:** Add MPI-enabled OpenMolcas variant

## Description

Adds `molcasMPI`, enabling OpenMolcas MPI support with external Global Arrays.

Includes a two-rank test checking parallel execution and HF, RASSCF and MS-CASPT2 reference energies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fc3403a3b7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.