# Issue

**Title:** Fix BoTorch recommendations with named candidate indices

## Description

### Summary

Preserve named candidate identities in discrete and hybrid BoTorch recommendation result reconstruction.

### Details and comments

When a search space is built from a dataframe with a named sample index (e.g. `material_id`), discrete recommendation crashes with `KeyError: 'index'` and hybrid discrete/continuous recommendation with `KeyError: "None of ['index'] are in the columns"`.

Both consumers call `candidates_comp.reset_index()` then look up the literal column `index`, but pandas uses the original index name instead. The fix uses a local opaque column label for the index carrier in the existing reset-index/merge reconstruction, so it cannot collide with parameter or computational column labels, and reads that same carrier in both discrete and hybrid paths.

Adds two regressions (discrete + hybrid) using real GP/BoTorch/qLogEI acquisition with named string indices, asserting configuration-to-sample identity mapping. Existing FAST_OPTIMIZATION_SETTINGS bound the work.

Verified locally: `pytest -q tests/test_campaign.py` 68 passed including both new regressions; ruff/format/flake8/pydoclint pass on changed files.

AI-assisted implementation; I supervised and checked the work as it progressed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95a94d5cc421`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.