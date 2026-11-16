# Issue

**Title:** bug in plotting function

## Description

@j3mdamas you can pretty much auto-accept this one. There is no `.data` in `MetricData`. It was a mistake in copy pasting some code from `Model`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2dddf3cf98a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.