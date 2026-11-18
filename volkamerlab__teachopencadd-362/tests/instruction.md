# Issue

**Title:** CI: Exclude T019 again from Windows CI

## Description

## Description
Remove T019 from our Windows CI as T019 cannot be run under Windows (and never has), see: 

## Todos
- [x] Update `ci.yml` so that CI for Windows skips T019
- [x] Add `dev` branch to the CI triggers for PRs, so that this PR will run the CI :)

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2b2e44d451e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.