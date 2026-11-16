# Issue

**Title:** Small Refactor of Exception Call Stack Size

## Description

## Description
This PR makes small changes to the `PsiException` class, specifically regarding the printout of the function call stack upon throwing. Now, the number of functions included in the printed call stack during exception printout is tied to a singular variable, instead of being scattered about in multiple places. The goal is to allow easier control of the function call stack size during printout for debugging purposes, if desired. 

There are a couple small cleanups here and there as well.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [X] N/A

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [X] All separate instances of function call stack printout sizes have been replaced with a single variable definition.
- [X] The `Stack` variable now uses a `std::array` instead of a `std::vector`.
- [X] Uses of `&Stack[0]` have been replaced with `Stack.data()`.

## Questions
- [X] N/A

## Checklist
- [X] Tests added for any new features
- [X] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [X] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8418efe67717`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.