# Issue

**Title:** expanding external_potential: parsing, take 2

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
replace half of #3272


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] `psi4.QMMMbohr` is further discouraged, and external point charges specification (always in Bohr, regardless of molecule units) now more flexibly takes in lists, numpy arrays, and psi4.core.Matrix es. (It also takes in more arrangements, but none of them will save keystrokes from the point charges case.)

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x]  As discussed at the 7 Feb Patkowski/Pederson/CDSgroup meeting, we want to route more user permanent potentials through the external_potential keyword (embedding charges in MBE). This is step 1 to allow point charges, diffuse charges, and (Nao, Nao) matrices to pass through, validated, with backwards compatible syntax. (diffuse and matrices are disallowed at the next step before hitting c-side.)
- [x]  Started trying to retire driver/qmmm.py, as the pb11 export of core.ExternalPotential should be sufficient. Fortunately, its direct use was already deprecated. Only MDI needed a line change. `QMMMbohr()` will raise a FutureWarning now
- [x] Filled in the test mark so `-m extern` runs all EP tests.
- [x] The `extern.cc` looks like a lot of changes, but it's really just hiding a block behind `if (charges_.size()) {...}` which is future prep.
- [x] Ubuntu image 20.04 has retired, so we're oging to have to bump testing from clang v6 (2018) to clang v11 (2020)

## Questions
- [ ] Question1

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7ea8293a918`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.