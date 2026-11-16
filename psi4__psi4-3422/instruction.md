# Issue

**Title:** Throw if Qmn_ is nullptr in DiskDFJK (in-core mode)

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
DiskDFJK and its derived objects have some footguns, and currently improper usage results in segfaults instead of an informative exception. I ran into this with @andyj10224 while working on DLPNO.
This PR does not fix the underlying issue of these objects arguably being a bit unergonomic, but at least the error message will be a bit better than a segfault.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] None, I think?

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] `manage_JK_core()` and `compute_JK()` in DiskDFJK now throw if called when the object is in a state where calling these functions would result in a nullptr dereference. (DiskDFJK is in in-core mode, and `Qmn_` is not a valid `shared_ptr` holding a ptr to a `Matrix`)
- [x] This PR also affects classes derived from DiskDFJK that do not override both of these functions, such as CDJK (only overrides  `manage_JK_core()` )

## Checklist
- [x] No new features
- [x] Tests run by the CI are passing

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d325b122ffd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.