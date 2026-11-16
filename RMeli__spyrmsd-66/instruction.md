# Issue

**Title:** Version 0.5.2

## Description

## Description

This PR provides several bug fixes and improvements related to `graph-tool`.


## Version 0.5.2

Date:            23/02/2022
Contributors:    @RMeli

### Fixed

* Inconsistent number of nodes with `graph-tool` for disconnected graphs [PR #61 | @RMeli]

### Improved

* Support for more types of node properties (including strings) with `graph-tool` [PR #64 | @RMeli]

### Changed

* `ValueError` exception into `NonIsomorphicGraphs(ValueError)` exception [PR #65 | @RMeli]

### Added

* Warning for disconnected graphs [PR #61| @RMeli]

## Checklist

- [x] Tests
- [x] Documentation
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e9cd9aa10af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.