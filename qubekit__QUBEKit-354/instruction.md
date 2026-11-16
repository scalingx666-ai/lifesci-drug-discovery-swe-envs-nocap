# Issue

**Title:** Fix optional stages

## Description

## Description
This PR fixes the running of workflows with optional stages. Fragmentation was introduced as an optional stage but only vsites were hardcoded as an optional stage meaning the workflow would error when ran with fragmentation as `None`. This is now fixed by checking each stage in the normal workflow and if that stage is `None` it is added to the skipped stages list. 

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [x] Test the workflow runs with optional stages

## Questions
- [ ] Question1

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a48d763f434f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.