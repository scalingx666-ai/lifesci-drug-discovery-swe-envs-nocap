# Issue

**Title:** Derivative/extrapolation enhancement

## Description

Hi Caleb,

This pull request implements the same extrapolation behavior as in extrapolate_integral. Tests were added too. There is a minor change in `plot_T_dependent_property` to allow extrapolation during a the `test_documentation_plots` test (calculate_derivative allowed for extrapolation before, but does not anymore).  

Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66c88645466a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.