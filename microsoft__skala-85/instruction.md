# Issue

**Title:** Atom-chunked evaluation of Skala 1.1

## Description

This PR does two things:
- adds evaluation of Skala 1.1 (exc, vxc, fxc) chunked by atom-grid. AO computation, feature computation and model evaluation are now chunked together, lowering peak memory.
  - For performance: Exc and vxc the atom chunks are packed together in larger chunks while still fitting in memory, for second order it is faster to run per atom chunk.
  - When on gpu: a helper routine sets the maximum chunk size specific for skala 1.1 based on number of AOs, grid size and order of the derivative of Exc. When on cpu: the available memory needs to set wchi goes via the usual `max_memory` parameter in PySCF
- Updates nuclear gradients to work with gpu4pyscf 1.6. With this update gpu4pyscf 1.5 is not supported anymore.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b69128dbf5f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.