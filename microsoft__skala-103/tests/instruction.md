# Issue

**Title:** Add analytic linear feature pullback

## Description

## Summary

- Add the `LinearFeature` abstraction for raw features that are linear in the density matrix.
- Add `MGGAFeatureFunction` for density, gradient, kinetic-energy density, and Laplacian features.
- Implement an analytic vector-Jacobian product from feature cotangents to symmetric density-matrix cotangents.
- Preserve restricted and spin-polarized batch shapes.
- Add focused tests covering:
  - every non-empty combination of supported meta-GGA features
  - density-matrix linearity
  - analytic VJP agreement with PyTorch autograd
  - restricted and two-spin density matrices
  - invalid feature specifications

This PR contains only the generic feature mathematics. Blockwise AO evaluation and spatial screening are introduced by the following PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb9d3a221c2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.