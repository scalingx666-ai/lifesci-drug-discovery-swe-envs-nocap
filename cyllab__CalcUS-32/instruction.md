# Issue

**Title:** Fixed cleaning of calculation orders (issue #31)

## Description

Default value of `c.last_seen_status` is 0, if calculation is not viewed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bef111160258`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.