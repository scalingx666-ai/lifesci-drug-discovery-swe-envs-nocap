# Issue

**Title:** Make symmetry codes ints and tuples

## Description

## Description
This PR fixes a bug in the valence type grouping method which used strings like `23-33` to build a bond type. The types were then clustered by checking the forward and reversed strings which would fail as the example bond type would become `33-32` and not be grouped correctly, tuples should avoid this issue.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [ ] TODO 1

## Questions
- [ ] Question1

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c170618eb55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.