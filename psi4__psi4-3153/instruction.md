# Issue

**Title:** Modernize relativistic potential

## Description

## Description
Paying off an old IOU. I'll get to what Francesco and Daniel Nascimento need after this PR is in.


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] `RelPotentialInt` now has the same charge field API as `PotentialInt` and should be faster

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] `RelPotentialInt` now delegates construction of W0 integrals to Libint
- [x] `RelPotentialInt` now has the same charge field API as `PotentialInt` 

## Checklist
- [x] `ctest -L x2c` passes

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `592d305938d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.