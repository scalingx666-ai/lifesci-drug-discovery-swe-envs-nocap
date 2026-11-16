# Issue

**Title:** BlockCoordinateOptimizer

## Description

First draft on the `BlockCoordinateOptimizer`:

- Introduces `BlockCoordinateOptimizer`, which allows stacking of multiple `OptimizerProtocol`
- Introduces `OptimizationSchedule`, an ABC for creating strategies on how to combine `OptimizerProtocol`s in the `BlockCoordinateOptimizer`
- Introduces `OptimizationStep` as one step in the `OptimizationSchedule`
- Introduces `CyclicOptimizationSchedule`, which cycles between `OptimizationStep`s. Inspired by botorchs [`optimize_acqf_mixed_alternating`](https://botorch.readthedocs.io/en/latest/_modules/botorch/optim/optimize_mixed.html#optimize_acqf_mixed_alternating)
- Adds convenience functionalities in the `SearchSpace`
- Adds tests
- Some type hinting changes to make everything work

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00f01902db44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.