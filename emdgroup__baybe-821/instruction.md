# Issue

**Title:** Refactor Campaign

## Description

## Removed Features
- `n_fits_done` and `FitNr` column tracking removed from `Campaign`; `n_fits_done` is now a deprecated property raising `DeprecationError`
- `n_batches_done` and `BatchNr` column tracking removed from `Campaign`; `n_batches_done` is now a deprecated property raising `DeprecationError`
- `_searchspace_metadata` field removed entirely (constants kept only for legacy deserialization)

## Renames
- `_measurements_exp` → `_measurements` (serialized key: `"measurements_exp"` → `"measurements"`)

## New Internal State Model
- `_recommended_experiments: pd.DataFrame` replaces `_searchspace_metadata["recommended"]`; filtering uses merge-based matching
- `_excluded_experiments: pd.DataFrame` replaces `_searchspace_metadata["excluded"]`; `toggle_discrete_candidates` adds/removes rows
- Measured state is now computed on-the-fly via `fuzzy_row_match` instead of persisted
- Empty DataFrames initialized with correct column schemas via `@field.default`

## Serialization
- Legacy `n_fits_done`, `n_batches_done`, `FitNr`, `BatchNr` fields silently discarded on load
- Legacy `"measurements_exp"` key migrated to `"measurements"`
- Legacy `searchspace_metadata` columns migrated:
  - `"recommended"` → `_recommended_experiments`
  - `"excluded"` → `_excluded_experiments`
  - `"measured"` discarded (since info already contained in `measurements`)

## Tests
- Removed `FitNr`/`BatchNr` assertions; refactored affected tests to use new state model
- Added deprecation tests for counters and legacy deserialization scenarios

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6fc3978c25a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.