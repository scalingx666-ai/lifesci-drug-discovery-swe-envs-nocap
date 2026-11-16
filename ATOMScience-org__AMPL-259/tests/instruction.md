# Issue

**Title:** Miscellaneous changes for 1.6.0

## Description

- Add full support for all XGBoost model parameters, including hyperopt searches.
- Add split_strategy output column to compare_models.get_filesystem_perf_results.
- Fix bug in setting response column weights to make it consistent across featurizers.
- Fix error handling in rdkit_easy.mol_to_html to return empty string rather than None.
- Only import datastore_functions module in functions that require it, so that atomsci-clients isn't required.
- Add script for patching model tarballs to point to local copy of training data (needed for AD computation).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7806b794937`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.