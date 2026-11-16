# Issue

**Title:** Reuse the JK object from SCF into FISAPT

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR makes it possible to pass a jk object from the initial HF calculation into FISAPT to avoid re-computing 3-index DF integrals. This is inspired by  by @Awallace3 and originates from the same discussion with @cdsgroup, but it is orthogonal - can work with or without the other PR.  

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] FISAPT computations will be slightly faster through re-using integrals

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [ ] A premade JK object is now passed to `fisapt_compute_energy()`.

## Checklist
- [ ] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96bfb215ae92`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.