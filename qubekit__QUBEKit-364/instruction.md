# Issue

**Title:** Integration testing

## Description

## Description
To avoid issues like #363 set up integration testing to run a fast full qubekit fit of ethanol to catch issues unit tests miss.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [x] run a full integration test on ethanol
  - [x] make sure torsions are fit?
  - [ ] make sure vsites are fit?

## Questions
- [x] Do we need a cheaper method for faster runs?

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69bac9b03ede`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.