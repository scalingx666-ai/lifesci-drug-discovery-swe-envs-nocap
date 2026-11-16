# Issue

**Title:** Adapt for QCFractal v0.65

## Description

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Not sure the exact mechanism of difference between qcfractal 0.64 and 0.65 (since I can see this error with psi4 src fixed, adcc pkg fixed, and qcel/qcng fixed ~0.50), but importing adcc under certain circumstances (snowflake) fails, causing the qcengine records to return as errors and the psi4 logic to fail.
- AI suggested some better error handling but going to defer that to #3034 . For now, just want to get CI working again.

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `144882d942e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.