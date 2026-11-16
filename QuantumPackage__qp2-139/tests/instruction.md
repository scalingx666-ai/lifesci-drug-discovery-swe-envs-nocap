# Issue

**Title:** Fixing converter for qmcpack and qp2 with pbc and excited states

## Description

Fixing the converter for QMCPACK and QP2 to handle properly PBC with phase factor and unfolding orbitals in supercells.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f9c398ffcfb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.