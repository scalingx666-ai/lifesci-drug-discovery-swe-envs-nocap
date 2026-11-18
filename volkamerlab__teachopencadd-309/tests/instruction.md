# Issue

**Title:** T021/22: Run under global environment

## Description

## Description
Fix #289 and investigate how env for T021 and T022 could work.

## Todos
- [x] #289 
- [x] Make env work for T021 and T022 (run CI only for those notebooks)
- [x] At the end: Run full CI again.

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cec5d3b9a45e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.