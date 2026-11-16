# Issue

**Title:** Plotting changes to use CVD-friendly colors and correct split subset distances

## Description

Changes to plotting functions in perf_plots, split_response_dist_plots and compare_splits_plots modules for two purposes:

- Make sure that semantic colors are distinguishable by users with color vision deficiency (CVD).
- Change Tanimoto distances in compare_splits_plots from one per training compound to one per validation or test compound.

Also update tutorials 3 and 9 to generate plots with new code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd0f80af7cc5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.