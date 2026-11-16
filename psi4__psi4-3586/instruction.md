# Issue

**Title:** Support ArrayType<string> options with non-empty defaults

## Description

## Description
This MR adds some features needed to get ArrayType<string> options with non-empty defaults operational.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
None! This is a technical infrastructure change.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Simplified overcomplicated pointer operations
- [x] Provided new liboptions overloads
- [x] Commented the difference between Data and DataType

## AI
- [x] None, except speeding up google searches

## Checklist
- [ ] No tests - this feature is needed by the GauXC PR, so that'll serve as the test. Unit tests are inappropriate, since in the age of AI, I imagine that we'll be replacing liboptions in short order, much as with libpsio and libiwl

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62222c5adfa9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.