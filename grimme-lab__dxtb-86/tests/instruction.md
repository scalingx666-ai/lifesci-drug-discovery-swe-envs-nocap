# Issue

**Title:** Separate Overlap class

## Description

- move the calculation of the overlap outside the Hamiltonian
- fix the indexing error in the overlap calculation by re-calculating references with tblite 0.3.0
- force 1.0 on diagonal of overlap (via torch.fill_diagonal_(1.0))

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `687d57609e6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.