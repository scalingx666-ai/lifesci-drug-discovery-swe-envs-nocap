# Issue

**Title:** Fix GPU gradients and Molden export for near-linear dependencies

## Description

The CUDA-only sign flip of the MO coefficients (scalarMatMul) used the wrong dimensions when NBSuse < nbasis, which corrupted the energy-weighted density and gave wrong GPU gradients; the flip is unnecessary because MO signs are arbitrary and every quantity that uses them is quadratic, so it is removed along with scalarMatMul. The Molden exporter now writes NBSuse orbitals instead of nbasis, so it no longer reads past the end of co/cob.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5179b0d954a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.