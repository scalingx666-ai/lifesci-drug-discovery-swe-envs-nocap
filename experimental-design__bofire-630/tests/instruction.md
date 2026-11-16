# Issue

**Title:** Fix/628

## Description

This PR addresses #628.

It adds a field to the data-model of the `BotorchStrategy`: `include_infeasible_exps_in_acqf_calc`

- This flag changes the behavior of the `get_acqf_input_tensors` function: Filtering out infeasible experiments (violation of constraints or bounds) will only be done, if the field is set to False.

- The default value is False, so the function will work as before, if nothing is changed.

- All `make` methods from the strategy classes, inheriting from `BotorchStrategy` are adapted to show this option in the kwargs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b14120c10d19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.