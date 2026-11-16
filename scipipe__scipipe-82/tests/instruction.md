# Issue

**Title:** Use Channels to Handle Task Order

## Description

Replaces the `tasks` slice in `Process.Run` with a channel. This allows completed tasks to be reaped while still processing in order. 

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34de3676a59b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.