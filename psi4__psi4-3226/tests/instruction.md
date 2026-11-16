# Issue

**Title:** MBIS valence charges

## Description

## Description
Prints out the MBIS valence charges. These were already being computed, just not exposed to the user. Tests were added for the new output, and all tests pass. There is no impact on runtime because it is just exposing values already being computed.

Addresses 

## User API & Changelog headlines
- [x] MBIS valence charges are now exposed and printed in MBIS output
- [x] The wfn array_variable `MBIS VALENCE CHARGES` is now available to be retrieved

## Dev notes & details
- [x] Saves the MBIS valence charges to it's own little matrix
- [x] And exposes those charges on the python side as the wfn variable `MBIS VALENCE CHARGES`
- [x] Updates the relevant tests

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `36ddfd822798`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.