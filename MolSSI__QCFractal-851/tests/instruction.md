# Issue

**Title:** Managers claiming/returning should be marked as modified

## Description

## Description

When a manager claims or returns tasks, that should count towards the server as having heard from the manager (for heartbeat purposes). Without this, a manager could get stuck returning or claiming lots of data, but then be marked as inactive by the server since the heartbeat mechanism has been block by the other actions.

This is a bit of a bandaid. The next iteration of the manager should probably use a separate threads for heartbeat and updates, which would also help.

Hopefully helps with #850 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `548f72f71464`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.