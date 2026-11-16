# Issue

**Title:** fix README formatting and avert libatomic and pubchem problems

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
nope

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] fixed spacing in README
- [x] forgive PubChem tests if they fail (pugrest too busy is popping up a lot lately). I'd like to do it more gracefully like in https://github.com/MolSSI/QCElemental/blob/master/qcelemental/tests/addons.py#L64 , but I think they'd have  to be moved from ctest to fully pytest for that
- [x] fix CI that's a problem on Mac for libatomic with latest einsums release 

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aaef3bfc2822`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.