# Issue

**Title:** abstract classes need ABCMeta

## Description

This fixes the lack of enforcing of the abstract methods of `Projection` which lead to `MetricCoords` passing the tests (but would have crashed if used with `Metric` since it lacked the `_precalculate` method)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f88b3556bda8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.