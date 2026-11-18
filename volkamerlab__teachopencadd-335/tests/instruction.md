# Issue

**Title:** Docs CI: switch to linkinator

## Description

## Description
Switch from `broken-link-checker` to `linkinator`. The former seems to be dead.

## Todos
Notable points that this PR has either accomplished or will accomplish.
- [x] Check all dead links

## Questions
- [x] What's the reasoning behind the excludes?

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2eecfe9f2046`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.