# Issue

**Title:** Add gradients and threading for diffuse charges

## Description

## Description
This pull request contributes gradients, extern-extern interaction energies, and OpenMP parallelization to the implementation of diffuse charges as external potentials. Much work has been performed recently to restore diffuse charges, including #3291 (parsing diffuse charges as possible inputs for the `external_potentials` keyword), #3272 (pytest for diffuse charges and exposing `BasisSet::convert_sap_contraction` to the Python layer to correct diffuse basis normalization), #3222 (preparing inputs for the `ExternalPotential` object), and #3372.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Users can get the analytic gradient of the energy for molecules in the presence of diffuse charges.
- [x] Users can get the analytic gradient of the energy for embedded diffuse charges by calling `ExternalPotential.gradient_on_diffuses()`, as with point charges in #3087.
- [x] Users can get the interaction energy between diffuse/point charges in separate `ExternalPotential` objects via `ExternalPotential.computeExternExternInteraction()`.
- [x] Evaluations for diffuse charges involving ERIs have been parallelized.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] The addition of `BasisSet::convert_sap_contraction` in `export_mints.cc` is the same as in #3272 and #3372.
- [x] Added the `ExternalPotential::gradient_on_diffuses_` attribute, which is populated during a gradient call and is accessible by the `ExternalPotential::gradient_on_diffuses()` method.
- [x] The diffuse charge component of the `ExternalPotential::computePotentialMatrix()` evaluation has been threaded.
- [x] The diffuse charge components of the `ExternalPotential::computePotentialGradients()` evaluation have been added and threaded.
- [x] Diffuse-point charge and diffuse-diffuse interactions have been added to the `ExternalPotential::computeExternExternInteraction()` evaluation.
- [x] Several variable names have been modified in `extern.cc` to maintain internal consistency and legibility/interpretability. For example, `nthreads` and `rank` have been made standard in setting up OpenMP loops; the external point charge and nuclear charge-field objects have been named `Qxyz` and `Zxyz`, respectively; and the number of basis functions has been renamed from `n` to `nbf`.
- [x] Test extern7 was added to the test suite, which compares the energy and gradients calculated for several systems using diffuse charges against limiting cases or analytically derived results.

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

Edit: I had originally mixed up #3222 and #3372.

LAB added:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ebac43fcee67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.