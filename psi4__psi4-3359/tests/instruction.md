# Issue

**Title:** Fix deprecation warnings + cleanup in `libfock`

## Description

## Description
This PR fixes the deprecation warnings that I found in `libfock` and also adds some functions to `libpsio` to support these changes.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Fixes several deprecation warnings involving Dimension casts to pointer in `libfock`.
- [x] Fixed `sprintf` deprecation warnings in `libfock`.
- [x] `libfock` migrated to replace `char *` with `std::string`
- [x] `libpsio` received new lightweight converters from `std::string` to `char *`  

## Checklist
- [x] Quicktests pass

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b7ec5c34619`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.