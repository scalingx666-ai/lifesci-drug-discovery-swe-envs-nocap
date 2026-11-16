# Issue

**Title:** NWChem wrapper fix

## Description

- [x] Throw exception if no conformers of a species have an energy or atoms when calling _set_lowest_energy_conformer()

- [x] Fixes NWChem Hessian extraction for >3 atoms

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f1c2f626ba0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.