# Issue

**Title:** add ResultProtocols.logfile

## Description

## Todos
  - [x] following slack discussion, use a protocol to control stdout return rather than `return_output` field (which doesn't validate with no extras)
  - [x] move `DriverEnum` up to `models`. I import it a lot, and most else is common_models was accessible

## Questions
- [ ] This could be made an enum and control stdout/stderr/other returned files. But keeping it simple for now.

## Status
- [x] Changelog updated
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abcbc004873e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.