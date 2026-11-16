# Issue

**Title:** Add pre-fitted atomic Gaussian parameter loader and data

## Description

2nd PR for **Improvement of the robustness of poisson equation**

This pull request implements a zero dependency loader` load_atomic_gaussian_params`(element) in src/grid/coulomb.py to retrieve pre-fitted $s$-type Gaussian parameters (coefficients and exponents) for elements H, C, N, O, and Cl from a package-safe JSON dataset `(atomic_gauss_params.json).` The loader supports case insensitive, space stripped element symbols (e.g. "cl", " C ") as well as atomic numbers (e.g. 17), utilizing a module-level lazy cache to avoid repeated disk reads. The packaging configuration in `MANIFEST.in` has been updated to bundle the dataset, the loader has been exported at the package root level, and unit tests have been added to verify type handling, lookup correctness, and parameter validity.

related to issue ->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `408bda10c3d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.