# Issue

**Title:** Update aug-cc-pvtz-dk

## Description

## Description
This PR updates the `aug-cc-pvtz-dk` basis set to include all supported elements in basis set exchange. Note that the `diff` shows many changes which are rearrangements between the current basis set exchange output and the older version from which the current `.gbs` file was sourced. I manually rearranged the basis set functions for the first few atoms to highlight this fact. 

Note that the existing .gbs file appears to be for `cc-pvtz-dk` in error rather than `aug-cc-pvtz-dk`, like the label. There are a few extra basis functions added for previously supported elements to accommodate the diffuse functions.

## User API & Changelog headlines
- [x] Update aug-cc-pvtz-dk to include diffuse functions for all atoms and support for Mo, Nb, Pd, Rh, Ru, Tc, Y, and Zr

## Dev notes & details
- [x] Update aug-cc-pvtz-dk.gbs file to include diffuse functions for all atoms and support for  Mo, Nb, Pd, Rh, Ru, Tc, Y, and Zr

## Checklist
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [X] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86f57edd1fb2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.