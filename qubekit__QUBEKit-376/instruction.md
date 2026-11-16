# Issue

**Title:** Fragment force field fix

## Description

## Description
This PR fixes an issue with fragment force fields which can have duplicate parameters when the smirks are made using `chemper ClusterGraph` and have to match every interaction instance (bonds, angles etc..) of the same type (symmetry equivalent). Now we use `SingleGraphs` built for a single instance of the interaction, these then transfer automatically to equivalent types of interactions.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [X] test on CHEMBL3264995 syk
  - [X] add tests

## Questions
- [ ] Question1

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2023ddff27bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.