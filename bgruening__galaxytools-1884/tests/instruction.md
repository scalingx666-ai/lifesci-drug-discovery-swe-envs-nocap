# Issue

**Title:** Update 3Dtrees standardization to v1.2.0

## Description

## What changed
- Updates the 3Dtrees standardization wrapper to `3dtrees-pc-standard` v1.2.0.
- Adds the optional `--approx-location` tuple input for collection mode.
- Expands collection-mode tests for no CRS, mixed CRS, invalid/untransformable CRS, and centroid metadata handoff fields.
- Adds small LAZ fixtures for no-CRS and invalid-CRS negative paths.

## Why
The v1.2.0 tool release reports collection centroid availability explicitly and keeps untransformable CRS cases from crashing mixed-geometry handling. Frontend workflows can use `centroid.available=false` to require an approximate location.

## Validation
- Built local `ghcr.io/3dtrees-earth/3dtrees-pc-standard:1.2.0` from the released tool source.
- Ran `planemo test --docker tools/3dtrees_standardization/standard.xml` from the clean PR branch: all 6 tests passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98179300a743`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.