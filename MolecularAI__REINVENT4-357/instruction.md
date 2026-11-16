# Issue

**Title:** fix: scoring components backfill missing scores with NaN instead of raising

## Description

A scoring component may return fewer scores than the number of input SMILES (e.g. an unparseable fragment) or omit some SMILES entirely. This previously raised a `RuntimeError` in `compute_component_scores` and in `compute_transform`, terminating the run.

## Changes
- `reinvent/scoring/compute_scores.py`: warn instead of raising on short results; backfill missing scores with NaN (the documented failure marker, see `ComponentResults` docstring) in `compute_transform`.
- `reinvent_plugins/components/component_results.py`: `fetch_scores`/`fetch_metadata` return NaN / None for SMILES that were never scored instead of raising `KeyError`, so the TensorBoard and CSV reporters continue on incomplete results.

## Tests
- regression tests: short results warn instead of raising, `fetch_scores` NaN for missing SMILES, `fetch_metadata` None for missing SMILES.

`pytest tests/scoring/unit_tests/test_compute_scores.py` -> 9 passed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee0d56f4a074`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.