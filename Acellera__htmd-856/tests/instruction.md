# Issue

**Title:** Small improvements to LSF and Slurm queues

## Description

Description:

- LSF and Slurm queue parameters that are lists fixed with ensurelist
- docstrings updated from protocolinterface with _printDocString()

To prevent error situations when passing a single value list (i.e. just a string), which is accepted by `protocolinterface` with `nargs=*`, but gets screwed on for loops.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0222b2a56a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.