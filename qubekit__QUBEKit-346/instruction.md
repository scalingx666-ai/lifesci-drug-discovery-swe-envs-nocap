# Issue

**Title:** Fix offxml library charges

## Description

## Description

This PR changes the library charges SMIRKS generation to use Chemper to ensure the patterns are specific enough to stop the miss application of the charges. This was found to happen with basic SMARTS patterns during mixture fitting when two molecules are included in the offxml and one is a substructure of the other. 



## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [x] Use Chemper to generate the smirks for library charges using the entire molecule
  - [x] Test miss application of parameters

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31760557d8ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.