# Issue

**Title:** Fix empty metadata bug in SmilesAssociatedComponentResults

## Description

## Description
Fixes a bug where `SmilesAssociatedComponentResults` would fail when `ExternalProcess` returns empty metadata.

## Problem
When an external script returns only prediction scores without additional metadata fields, the `metadata` dict is empty (`{}`). The `_score_lists_to_dict` function was using `zip(*metadata.values())` which fails on empty dicts.

## Solution
- Check if metadata dict is empty before attempting to zip
- Return empty dict for each SMILES when no metadata present
- Add comprehensive tests covering empty metadata scenarios

## Tests Added
- `test_externalprocess_empty_metadata`: Main bug reproduction test
- `test_externalprocess_with_metadata`: Existing functionality test
- `test_externalprocess_multiple_endpoints_empty_metadata`: Edge case test
- `test_externalprocess_metadata_variations`: Parametrized tests for various scenarios

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa7934ff2411`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.