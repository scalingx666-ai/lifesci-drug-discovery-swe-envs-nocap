# Issue

**Title:** Saptdft reuse jk for scf

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Previously, SAPT(DFT) `scf_helper()` calls would re-compute integrals for SAPT0 dimer and monomer computations. Furthermore, the DFT `scf_helper()` calls would also recompute 3-index integrals by regenerating the JK-object. This PR enables developers to pass in a jk object to scf_helper to not re-compute 3-index DF integrals if desired. This change was largely drafted during a meeting between @cdsgroup with @konpat on Dec. 13th, 2024. Further tested in a 7 Feb 2025 meetup.



## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] SAPT(DFT) and SAPT(HF) computations will be faster through re-using integrals on SCF's

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Added kwargs option of passing a JK-object to `scf_helper()` to prevent re-computing integrals for SCF.

## Questions
- [x] Question1

## Checklist
- [X] Passes previous sapt-dft1 tests
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96bfb215ae92`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.