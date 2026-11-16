# Issue

**Title:** Feature/base tl regr benchmark

## Description

**Base class for transfer learning regression benchmarks and core benchmark loop**

 This PR implements the new `TransferLearningRegression` benchmark class in `benchmarks/definition/regression.py` and the main benchmark loop in `benchmarks/domains/regression/base.py`. To create a new regression benchmark, one needs to implement three functions for the specific problem (`load_data_fn`, `create_searchspaces_fn`, and `create_objective_fn`) and call `run_tl_regression_benchmark`. This interface allows new regression benchmarks to reuse existing functionality from the transfer learning convergence benchmarks.

 Once we agree on the overall logic, an example will follow in the next PR that converts an existing transfer learning convergence benchmark into a regression benchmark.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12df0ca7d5a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.