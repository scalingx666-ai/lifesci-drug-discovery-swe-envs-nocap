# Issue

**Title:** Fix deprecation warnings + cleanup in `libscf_solver`

## Description

## Description
This PR fixes the deprecation warnings that I found in `libscf_solver` and also does some miscellaneous code cleanup. Please pay attention to my changes in the level shift procedure.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Fixes several deprecation warnings involving casts to pointer in `libscf`.
- [x] This PR does create a merge conflict with #3351 because the `HF::form_Fia` signature changes. The solution of this PR is preferred.

## Checklist
- [x] Quicktests pass

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d44eaf840fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.