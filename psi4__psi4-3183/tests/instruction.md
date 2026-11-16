# Issue

**Title:** Replace SplitJK method-specific functions with typecasts

## Description

## Description
This PR was motivated by a comment by @andyj10224 in PR  pointing out that implementing method-specific setters/getters in `SplitJK` could more elegantly and sensibly be performed via downcasting. While the comment in that PR addressed knobs specific to `snLinK`, it is also applicable to other methods within the CompositeJK framework. This PR fixes that, replacing all instances of method-specific setters/getters in the base `SplitJK` class with downcasting to call the needed function at the derived-class level.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [X] Renames `COSK::set_COSX_grid` and `COSK::get_COSX_grid` functions to `COSK::set_grid` and `COSK::get_grid`, respectively.
- [X] Removes `SplitJK::set_COSX_grid` and `SplitJK::get_COSX_grid` functions. 

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [X] Removes `SplitJK::set_COSX_grid` and `SplitJK::get_COSX_grid` functions, localizing their presence to the `COSK` class.
- [X] Replaces utilizations of the above with usage of downcasting in the `CompositeJK::set_COSX_grid` and `CompositeJK::get_COSX_grid` functions.

## Questions
- [X] N/A

## Checklist
- [X] Tests added for any new features
- [X] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [X] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `079ac2398a57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.