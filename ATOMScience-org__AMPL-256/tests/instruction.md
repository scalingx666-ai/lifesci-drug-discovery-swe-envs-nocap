# Issue

**Title:** Perf plots

## Description

I updated 
- compare_splits tanimoto distance histograms to be matplotlib axes instead of seaborn facet grids
- perf_plots now have two more plots to plot predicted_vs_actual from a dataframe or from a model tarball
- still needs the comparable plots for classification models (#254)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7806b794937`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.