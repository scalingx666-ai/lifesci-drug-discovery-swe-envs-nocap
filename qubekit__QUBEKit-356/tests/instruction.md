# Issue

**Title:** Volume unit fix

## Description

## Description
This PR fixes the units for the AIM volumes to be in bohr^3 as they should be. Currently, they are set as angstroms^3 and then requested in angstroms^3 so no conversion happens, this fix will break old offxml files with incorrect units. 

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [x] Make sure that values are consistent with new offxml files

## Questions
- [ ] Question1

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d76cc3f8c44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.