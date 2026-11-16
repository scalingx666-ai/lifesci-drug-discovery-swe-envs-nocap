# Issue

**Title:** Fix analytical forces in electric field

## Description

`forces_analytical` ignored the electric field, which gave force errors of about 1e-2 for a field of 0.01-0.02 a.u. (neutral and charged systems alike). Two contributions were missing:

- The monopolar term -q_A F. `ElectricField` did not implement `get_atom_gradient` and fell back to the zero gradient.
- The dipole integral derivative. The GFN1 Hamiltonian gradient does not use the dipole potential. It is now evaluated for a fixed density via autograd through the dipole integral.

Autograd forces were not affected. The new tests compare analytical against autograd forces for NO2- and a SiH4/NO2- batch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ab7e7970674`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.