# Issue

**Title:** TorsionDrive scratch fix

## Description

## Description
This PR makes the scratch folders in the torsiondrive engine have a unique job id to ensure they are not shared between QM processes. The folders are now also removed once the torsiondrive is complete and a minimal number of files are saved which encode the whole torsiondrive.


## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `22de2539afe4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.