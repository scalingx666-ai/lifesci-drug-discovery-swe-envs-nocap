# Issue

**Title:** Fix Polars Deprecation Warnings

## Description

Since likely `1.42.0` polars throws deprecation warnings for usage of `.explode()`, causing CI [failure](https://github.com/emdgroup/baybe/actions/runs/28647289944/job/84957104109?pr=850#599) for us

The corresponding polars expressions have been reworked to be simpler and avoid `explode`. A minor version bump for polars was needed due to the availability of `list.n_unique`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ccbab7799c9d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.