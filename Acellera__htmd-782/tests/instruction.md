# Issue

**Title:** Refactor configuration and logging

## Description

- [x] Fix argument printing
- [x] Refactor `queue` and `qm` configuration
- [x] Refactor `Molecule` logging
- [x] Factor out `getEquivalentsAndDihedrals`
- [x] Refactor dihedral selection
- [x] Disable multi-FF parameterization
- [x] Factor out `_get_initial_parameters`
- [x] Factor out `_output_results`
- [x] Fix #494
- [x] Fix #549

~~Depend on #788~~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0296e173587e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.