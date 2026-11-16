# Issue

**Title:** Refactor/Chore: Remove metrics and evaluation from BenchmarkV2Specification

## Description

This pull request remove metrics from 'BenchmarkV2Specification' and removes client side evaluation. 

### Core Framework Updates:
* Refactored `PredictiveTaskSpecificationMixin` to remove metrics-related fields and added a new `task_type` property for high-level task categorization. (`polaris/benchmark/_task.py`) 
* Introduced `PredictiveTaskSpecificationMixinWithMetrics` to maintain backwards compatibility for benchmarks requiring metrics (V1) and updated imports and class definitions to use this mixin where applicable. (`polaris/benchmark/_base.py`, `polaris/competition/__init__.py`). 
* Refactored  `BenchmarkV2Specification` to inherit directly from `PredictiveTaskSpecificationMixin` and `BaseArtifactModel`, bypassing the middle `BenchmarkSpecification` abstraction. (`polaris/benchmark/_benchmark_v2.py`)


### Test Updates:
* Updated test cases to reflect the removal of metrics from BenchmarkV2. (`tests/conftest.py`, `tests/test_benchmark_v2.py`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74f7b809db64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.