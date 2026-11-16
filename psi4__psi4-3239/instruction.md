# Issue

**Title:** Fix EMBPOT Functionality in SCF and Add EMBPOT Gradients

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This pull request fixes the functionality of the EMBPOT perturbation to the core Hamiltonian in SCF calculations and adds appropriate gradients for the EMBPOT potential.

The EMBPOT perturbation works by reading x, y, z, w, and v coordinates from a file (`EMBPOT`) during the call to `HF::form_H()`. The core Hamiltonian of the `HF` object is then modified to include a contribution that is calculated by performing numerical integration of the basis over the EMBPOT coordinates, weights, and potentials. This functionality assumed that the values of phi calculated in the `BasisSet::compute_phi()` routine are always in a cartesian basis and not in a spherical basis, which was true up until the fix in #2210, which was included in the 1.4 release. Accordingly, an unnecessary AO to SO transformation is applied in the `HF::form_H()` routine every time, which results in inaccurate EMBPOT matrices being added to the core Hamiltonian. In order to correct this in the current version of Psi4, I have removed the AO to SO transformation and call `BasisSet::compute_phi()` on an appropriately sized vector. I have also added numerical gradients over the EMBPOT potential using the gau2grid library.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] The user may supply an arbitrary potential evaluated on a numerical quadrature grid to an SCF calculation by saving the x, y, z, w, and v values to a human-readable `EMBPOT` file. The first line of the `EMBPOT` file must have the number of points inside of the file. The user must also include `set perturb_h true` and `set perturb_with embpot` in the Psi4 input. The potential will then be evaluated and included in the core Hamiltonian construction, and energy and gradient calculations.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Fixed the EMBPOT functionality in `HF::form_H()` by removing AO to SO transformation and supplying an appropriately sized vector to the `BasisSet::compute_phi()` call.
- [x] Added function `MintsHelper::embpot_grad()` to calculate the component of the gradient from the EMBPOT perturbation.

## Checklist
- [x] Added test `embpot1` to compare energies and gradients computed by including embedded point charges analytically, through the `external_potentials` keyword, and numerically, through the EMBPOT functionality.
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `228c142ab191`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.