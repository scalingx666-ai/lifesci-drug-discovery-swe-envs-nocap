# Issue

**Title:** fix CI on Windows

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] QCFractal now available for Py 3.14

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] ~New gcp problems so see if can avoid by pinning to longstanding 2.3.2~ False diagnosis
- [x] There was a windows infra set of new packages that were bad, so pinning for now 
- [x] New qcfractal v0.70 this week, so reengage snowflake tests for py314


## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `886caaabe23d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.