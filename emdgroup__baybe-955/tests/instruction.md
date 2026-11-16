# Issue

**Title:** Use marginal posteriors for SHAP explanations

## Description

.

SHAP needs posterior means, but its callbacks request joint posteriors. This builds an unnecessary covariance matrix and rejects multiple rows for independent Gaussian surrogates.

I use marginal posteriors in both representations and preserve the sample dimension when removing the singleton output dimensions. The regression covers mean, Bayesian linear and Gaussian-process surrogates, categorical inputs, single and multiple rows, posterior input shapes and explanation additivity.

Validation:

- All 305 SHAP tests pass. The 12 regression cases fail on unchanged main and pass with this fix.
- The full suite has 2,883 passes and three skips. It retains the same `test_random_seed_adoption[True]` failure as unchanged main (2,871 passes, three skips).
- `tox -e typecheck-py310` and pre-commit checks pass.

cc @Scienfitz

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b3149948d1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.