# Issue

**Title:** pyeinsums avail in psi

## Description

## Description
Build or detect and test Python Einsums interface in Psi4

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Make python interface to Einsums available to Psi4 by (1) building it if otherwise building c++ Einsums, (2) installing the pyeinsums conda pkg as an addon, (3) copying some basic matrix tests to pytests to exercise in the Py intf.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] relevant PRs
  - [x] 
  - [x] 
  - [x] 
- [x] work is mostly done, just need to pull in at various repos so not using one of my branches. While `-D ENABLE_Einsums=ON` ensures the c++ intf is available, I can't promise the same for py intf availability since cmake doesn't know about it in einsumsconfig.cmake
- [x] avert a problem with the ecosystem tests where one of the addons (perhaps resp) brings psi4 the conda package as a dependency. now psi4 is uninstalled just in case.

## Checklist
- [x] Tests added for any new features
- [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d44eaf840fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.