# Issue

**Title:** Fix initial cartesian units

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR  . Basically the psithon way of defining molecules converted _initial_cartesian on parsing.
When adding an external potential this was used as
molecule.set_geometry(clone_molecule._initial_cartesian).
set_geometry applies the conversion again.

The two python ways I found, which set initial_cartesian did not do the conversion leading to incorrect geometries, when using external_potential and molecules defined as unit=angstrom.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] : Parsing molecules with angstrom units and using external_potential from python was broken

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] : Parsing molecules from psithon and python left mol._initial_cartesian in a different unit. This aligns the units. Downstream this had the effect of breaking using molecules with angstrom units with an external_potential from python

## Questions
- [x] Question1

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0a457663fc8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.