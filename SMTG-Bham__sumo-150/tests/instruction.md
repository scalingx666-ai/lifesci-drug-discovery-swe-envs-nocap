# Issue

**Title:** FIX: Improve averaging of optical spectra

## Description

Currently, optical properties (absorption, refractive index, loss, etc) are averaged using only the trace of the dielectric tensor. I've refactored the implementation to instead average the eigenvalues of the respective tensors. I think this should improve the averaged optical properties for non-orthogonal lattices, as these can contain off diagonal elements of the dielectric tensor.

The new implementation now does all the property calculations on the tensors and only averages at the last minute. I've also added support for extracting the full tensor, eigenvalues, and trace, rather than just averaged or not-averaged.

Note that I had to edit the test data for Ge. Strangely, this calculation has off diagonal dielectric components even though it is in the cubic space group... Perhaps the primitive cell is not aligned with the cartesian axes correctly.

@ajjackson does this look reasonable?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fa4f38b5210`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.