# Issue

**Title:** Try bumping macos-x86 version to 15 in CI

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
MacOS 13 is gone from CI and 14 will be gone in a year or so.
Try 15.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [ ] RN 1
- [ ] RN 2

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [ ] Feature1
- [ ] Feature2

## Questions
- [ ] Question1

## Checklist
- [ ] Tests added for any new features
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [ ] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08b9c431fa25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.