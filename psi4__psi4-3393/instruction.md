# Issue

**Title:** needs_grac_ is now computed rather than cached. code modernization.

## Description

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] `needs_grac_` variable is removed in favor of a `needs_grac` method
- [x] Miscellaneous code modernization - lots of range based for loops and auto 

## Checklist
- [x] `grac` test and dft smoke still passes

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc501abf3023`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.