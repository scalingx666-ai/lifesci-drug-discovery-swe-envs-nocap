# Issue

**Title:** Arbitrary 1-electron potential matrices for SCF

## Description

## Description
This pull request adds the ability to provide an arbitrary, pre-calculated one-electron potential matrix for an SCF calculation through the `external_potentials` keyword.

This replaces #3243 and addresses #3227 and #3149. Based on the discussion at the 7 Feb 2025 Patkowski/Pederson/CDSgroup meeting, it was determined that the possible inputs to the `external_potentials` keyword could be expanded to accommodate both pre-computed one-electron potential matrices and diffuse charges. This pull request implements the former, and a pull request for the latter is forthcoming. The input parsing and validation for this use of the `external_potentials` keyword was added in #3291.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] The user may provide an arbitrary one-electron potential matrix to the `external_potentials` keyword used during calls to the `energy` or `gradient` functions, given that it is provided as the third item in a `list` (using `None` for the first two items of the list if no point charges or diffuse charges are used, respectively) or as the value to the `"matrix"` key of a `dict` (details in #3291). The matrix can be provided as a list of lists or a NumPy array, much like the existing options for point charge input.
- [x] The `ExternalPotential::computePotentialGradients()` method has been exposed in the Python layer, allowing the user to readily calculate the Hellmann-Feynman and nuclear components of the gradient for a `core.ExternalPotential` object given that it has point charges (this will be expanded to include the gradient contributions from diffuse charges). Hellmann-Feynman (and nuclear) gradient components are not calculated for arbitrary one-electron potential matrices (as discussed in #3322).

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Added the `ExternalPotential::matrix_` attribute and `ExternalPotential::setMatrix()` method to store and set a provided one-electron potential matrix. This setter is called in the `_set_external_potentials_to_wavefunction()` function defined in `driver/procrouting/proc.py`, after casting the user input to a `core.Matrix` object. The `ExternalPotential::matrix_` is then added onto the result of `ExternalPotential::computePotentialMatrix()`, provided that it is a square matrix with the correct (Nbf x Nbf) dimensions. The result of `ExternalPotential::computePotentialMatrix()` is added onto the core Hamiltonian in `HF::form_H()` before proceeding into the SCF loop.
- [x] The `ExternalPotential::computePotentialGradients()` method has been exposed in the Python layer.
- [x] Added a test `extern6` to the test suite, which compares the energy and gradient calculated from an SCF where a set of point charges was provided to the `external_potentials` keyword against those calculated from an SCF where the one-electron potential matrix evaluated with the same point charges was provided to the `external_potentials` keyword.

## Questions
- [ ] Should a warning occur when calling `gradient` that Hellmann-Feynman contributions are not included in the result when a one-electron potential matrix is provided to the `external_potentials` keyword? Given that pre-calculating an external potential matrix to be included in an SCF is an advanced user feature, I tend to think that it is not strictly necessary. Possible nuclear contributions and extern-extern interactions are also not calculated when calling `ExternalPotential::computeNuclearEnergy()` or `ExternalPotential::computeExternExternInteraction()`, respectively, due to the arbitrary nature of the potential.

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d8eac07ac32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.