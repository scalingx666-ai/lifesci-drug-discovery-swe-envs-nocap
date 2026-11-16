# Issue

**Title:** Fix many compiler warnings

## Description

## Description
Fixes many compiler warnings by no longer passing redundant arguments to Matrix constructors.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Fixes 83 compiler warnings, 81 of which were coming from `dct`.

## Checklist
- [x] quick tests and dct tests pass

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8418efe67717`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.