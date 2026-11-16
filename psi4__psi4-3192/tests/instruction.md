# Issue

**Title:** DLPNO-CCSD(T) Primer Part 1: Reorganize DLPNO Class Heirarchy

## Description

## Description
In preparation of the DLPNO-CCSD(T) code, I have changed the class heirarchy of the DLPNO module. Currently, there is only a `DLPNOMP2` class. However, I have split that class into a `DLPNO -> DLPNOMP2` inheritance heirarchy, to allow for 
`DLPNO -> DLPNOCCSD -> DLPNOCCSD_T` in the future, and potentially `DLPNO -> DLPNOMP2 -> DLPNOMP2_F12`

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Changes class heirarchy of DLPNO module
- [x] Changes the way the DOI grids are handled in DLPNO-MP2, adds separate user options for the DOI grid specifically

## Questions
- [ ] 

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7245e70546a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.