# Issue

**Title:** Be able to work without using NWChem's line search

## Description

<!-- Thank you for your contribution! -->

## Description
Fixes a bug where we retrieved only the initial geometry if you turn off the line-search option in NWChem's driver.

## Changelog description
Bug fix: Was retrieving only the first step in a geometry relaxation

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c93cd5e94ce7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.