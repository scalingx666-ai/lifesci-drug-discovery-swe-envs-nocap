# Issue

**Title:** fix: make get_halflife_points use lambda.z.time.last

## Description

Proposal to solve #448

This pull request makes changes to the `get_halflife_points` functionality to improve the accuracy of calculations by updating the reference for the last time point used in half-life determination (`tlast` > `lambda.z.time.last`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `165bbda605e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.