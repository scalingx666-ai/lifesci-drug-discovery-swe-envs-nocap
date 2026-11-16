# Issue

**Title:** Conformal Prediction Wrappers

## Description

Overview:
This PR introduces several new files to support conformal prediction in molecular machine learning pipelines, as well as comprehensive unit tests for pipeline and conformal prediction functionality.

conformal.py: Implements UnifiedConformalCV(single-model) and CrossConformalCV(aggregate CP) wrappers for easy conformal prediction (classification/regression) on top of scikit-learn models.
test_conformal.py: Unit tests for the conformal wrappers, covering both regression and classification.
test_pipeline.py: Unit tests for the main pipeline, including integration with conformal prediction.
advanced_04_conformal_prediction.ipynb: Example notebook showing conformal prediction on molecular data, with benchmarking and visualization.

How to test:
Run pytest on the new test files to verify correctness.
Open and run all cells in the notebook to see conformal prediction in action.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9a5a54e1eec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.