# Issue

**Title:** [WIP] Additional exx kernels: Voxel averaged and Wigner-Seitz truncation

## Description

Two additional useful strategies for the Coulomb kernel for electron repulsion integrals (e.g. for exx).

Wigner-Seitz truncation
[R. Sundararaman, T. A. Arias. Phys. Rev. B **87**, 165122 (2013)](https://doi.org/10.1103/PhysRevB.87.165122)

Voxel averaged (mean potential)
[T. Schaefer et al, J. Chem. Phys. 160, 051101 (2024)](https://doi.org/10.1063/5.0182729)
This requires Gauss-Legendre quadrature points, hence I added the package FastGaussQuadrature to the dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e19a00d28490`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.