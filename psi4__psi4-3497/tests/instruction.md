# Issue

**Title:** Fix cuEST DFT w/symmetry

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [ ] RN 1
- [ ] RN 2

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Fixed a buffer undersize and missing AO->SO back-transform so DFT non-C1 can run with symmetry. Removed temp cast. 
- [x] When cuEST enabled, the grid is built on the GPU, so add graceful exits to functions expecting to use the absent CPU grid
- [x] Added tests akin to dft1 and updated them with wK functionals
- [x] Added some GPU health diagnostics to help users disentangle GPU vs psi4/cuest errors.
- [x] Moved all the GPU and cuEST init to a separate file from core.cc

## Questions
<!-- Any questions or decision points on which you need clarification
     from the Psi4 team. -->
- [ ] Question1

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [ ] AI usage

## Checklist
- [ ] Tests added for any new features
- [ ] Docstring or narrative docs/sphinxman/source updated if needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [ ] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ed2db828307`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.