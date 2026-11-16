# Issue

**Title:** Added Hellmann-Feynman Gradients to NumIntHelper

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This pull request adds the ability to evaluate the Hellmann-Feynman gradient term for arbitrary potentials via numerical quadrature with the `psi4.core.NumIntHelper`.

At the 7 Feb Patkowski/Pederson/CDSgroup meeting, it was suggested that the user ought to be responsible for calculating the Hellmann-Feynman gradient component when supplying Nao x Nao matrices to the `external_potentials` keyword (#3291), since there is no way to determine how the gradient should be calculated from its potential integral matrix. The `psi4.core.NumIntHelper` can currently evaluate the potential integral matrices from an arbitrary potential. If these potential integral matrices are going to be able to be supplied to the SCF machinery, then adding support for evaluating the corresponding Hellmann-Feynman contribution to the gradient would be helpful to users.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] The user may evaluate the Hellmann-Feynman gradient term associated with an arbitrary potential via numerical quadrature with `psi4.core.NumIntHelper.potential_gradient()`. The potential must be supplied as a `list` of `psi4.core.Vector`, where each vector object corresponds to a block in the `psi4.core.DFTGrid` used to instantiate the `psi4.core.NumIntHelper`. A single density matrix must also be supplied.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Added function `NumIntHelper::potential_gradient()` to calculate the Hellmann-Feynman contribution to the gradient from an arbitrary potential via numerical quadrature. This function is primarily based on `RV::compute_gradient()` and `NumIntHelper::potential_integral()`. The function makes a call to a `gradient_integrator()` function, which is defined in the anonymous namespace of `libmints/numinthelper.cc` and is comparable to the `rks_gradient_integrator()` defined in `libfock
/dft_integrators.h`.
- [x] Added a test `numint1` to the test suite, which compares the numerical potential integral matrix (`psi4.core.NumIntHelper.potential_integral()`) and Hellmann-Feynman gradient (`psi4.core.NumIntHelper.potential_gradient()`) from a set of point charges against their analytic counterparts calculated by `psi4.core.ExternalPotential`.

## Checklist
- [x] Tests added for any new features
- [x] All or relevant fraction of full tests run

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6053f9aefa46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.