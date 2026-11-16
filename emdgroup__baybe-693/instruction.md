# Issue

**Title:** Enable automatic random seeds for simulation

## Description

#668 addressed the random seed issues in the simulation module only partially, i.e. it does not provide a solution for situations where the seed needs to be incremented when passing initial data to `simulate_scenarios`.

This PR takes care of it by adjusting the logic and default value of `n_mc_iterations` in a backward-compatible way:
* When `n_mc_iterations` takes an integer value, the Cartesian product of all possible rollouts is executed, i.e. each initial data set (if provided) is executed with each random seed
* When `n_mc_iterations` is set to `None`, one Monte Carlo iteration is executed per initial data set, but the seed is automatically increased for each rollout, to enable trajectory variation for simulations that do not depend on the initial data (e.g. when using non-predictive recommenders).

**Note:** The latter scenario can still be executed with *fixed* random seed since it's equivalent to the first when `n_mc_iterations=1`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc3cab32cd95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.