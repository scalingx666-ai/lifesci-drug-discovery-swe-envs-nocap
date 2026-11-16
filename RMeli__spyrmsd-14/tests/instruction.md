# Issue

**Title:** Caching Graph Isomorphism and Refactoring

## Description

## Description

* Refactoring of `rmsd.rmsd_isomorphic`
  * Removed `rmsd.rmsd_isomorphic_qcp`
  * Moved core functionality to `rmsd._rmsd_isomorphic_core`
* Added `multirmsd_isomorphic`
  * Cache graph isomorphism for multiple RMSD calculations (fix #11)
* Refactored `rmsdwrapper`
  * Cache graph isomorphism by default
  * Strip hydrogen atoms by default

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cca5d85ad19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.