# Issue

**Title:** fix(amplify): cap setuptools<82 to preserve pkg_resources

## Description

## Description

Fixes nightly CI failure in `unit-tests (models/amplify)` ([run #25911784459](https://github.com/NVIDIA/bionemo-framework/actions/runs/25911784459)).

### Root Cause

When `pip install -e .` runs for the amplify recipe, pip resolves `setuptools>=61.0` to v82.0.1. In setuptools 82+, `pkg_resources` was removed as a bundled module. The `hypothesis` testing library (installed in the base container image) imports `pkg_resources` in its `entry_points.py`, causing pytest to crash at startup:

```
ModuleNotFoundError: No module named 'pkg_resources'
```

### Fix

- Cap `setuptools>=61.0,<82` in `[build-system].requires`
- Add `setuptools<82` to `[project].dependencies` to prevent runtime upgrade

This preserves backward compatibility until either the base image is updated with a newer hypothesis that does not use `pkg_resources`, or setuptools-pkg-resources is added.

### Type of changes

- [x] Bug fix (non-breaking change which fixes an issue)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e870d311db95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.