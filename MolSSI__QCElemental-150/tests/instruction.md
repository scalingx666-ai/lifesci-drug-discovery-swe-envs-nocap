# Issue

**Title:** `which_import` now *really* handles submodules correctly

## Description

## Description
This is a correction on #144.
This correction also includes tests to ensure the behavior works as originally intended.

Apologies for the churn; I should have built some explicit tests in the first go-around. My bleary-eyed *ad hoc* tests were not a good substitute.

## Status
- [ ] Changelog updated
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67568689ebd6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.