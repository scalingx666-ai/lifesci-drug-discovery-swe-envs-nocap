# Issue

**Title:** Re-added dielectric; rfree reader; general cleanup

## Description

## Description
* Re-added dielectric command
* Re-added rfree param reader from FB output
* Saved n_workers, restart/end/skip to molecule (will be moved with config update)
* Moved virtual_sites.py to non_bonded
* Cleaned up configs
* Removed old or duplicated code
* Streamlined and clarified certain TODOs
* Various minor fixes

## Todos
  - [ ] Restart/end/skip commands will be moved some time after the config update, likely other commands will be moved too.
  - [ ] May need to provide a more long-term solution to rfree param reading.

## Questions

## Status
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e03a7d1863fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.