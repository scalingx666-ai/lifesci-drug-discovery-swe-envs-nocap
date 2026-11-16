# Issue

**Title:** Fix coordinate check

## Description

## Description
This PR fixes a recent testing failure caused when checking for coordinates before converting the QUBEKit Ligand to qcschema. The issue is caused by comparing a numpy array with an empty list, as we use pydantic to enforce the types we will always have a numpy array or `None` so we can just check the shape of the array.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [ ] TODO 1

## Questions
- [ ] Question1

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb13e66346cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.