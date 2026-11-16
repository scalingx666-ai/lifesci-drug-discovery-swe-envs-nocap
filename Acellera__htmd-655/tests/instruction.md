# Issue

**Title:** Fix multiplequeues

## Description

This was a big oversight from me. It  and concludes #580.

I've tested both `inprogress()` and `stop()` methods in both Slurm and LSF and this code works. I know you can only test Slurm and you'll have to trust me on LSF :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41b3719da548`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.