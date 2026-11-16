# Issue

**Title:** openqp: init at 1.3.1

## Description

Adds the OpenQP quantum chemistry program, which implements, among others, MRSF-TDDFT. https://github.com/Open-Quantum-Platform/openqp

OpenQP does the usual crazy things: use setuptools to call cmake to build fortran, where all Fortran and C dependencies are vendored via on-the-fly downloads, hardcoding BLAS and LAPACK vendors and so on and so forth. This PR includes quite some patches to break up the vendored dependencies, accept generic BLAS and make it compatible with a DFT-D4 version that is younger than 4 years ...

Unfortunately, it also requires a Libint rebuild, as it uses some Fortran headers from Libint, which are not installed by Libint. Admittedly its a mystery to me why these Fortran headers are not installed by default and possibly we could also think about doing that in the nixpkgs version of libint already to avoid rebuilds here.

cc @brohmsen let us know whether it works for you and calculations run as expected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0eb5ad9c848`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.