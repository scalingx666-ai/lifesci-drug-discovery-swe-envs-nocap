# Issue

**Title:** Create v3.0.1 Release

## Description

# Change Log

From v3.0.0 to v3.0.1

## Fixes
- Fixed a bug in `QSPRDataset` where property transformations were not applied.

## Changes

- renamed `PandasDataTable.transform` to `PandasDataTable.transformProperties`
- moved `imputeProperties`, `dropEmptyProperties` and `hasProperty` from `MoleculeTable`
  to `PandasDataTable`.
- removed `getProperties`, `addProperty`, `removeProperty`, now use `PandasDataTable`
  methods directly.

## New Features

## Removed Features

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b28f843943ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.