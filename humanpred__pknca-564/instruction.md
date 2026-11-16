# Issue

**Title:** fix: allow NA concentrations in sparse NCA

## Description

## Problem

`pk.nca()` aborts when sparse concentration data contains any `NA`. The error originates in `as_sparse_pk()`, which calls `assert_conc_time(any_missing_conc = FALSE)` — rejecting the entire dataset even if only one observation is missing.

```r
d_conc <- data.frame(
  subject = 1:6,
  time    = c(0, 0, 4, 4, 24, 24),
  conc    = c(0, 0, 5, 7, 3, NA)
)
# ...
pk.nca(o_data)
# Error: Assertion on 'conc' failed: Contains missing values (element 6).
```

## Fix

`as_sparse_pk()` now accepts `NA` concentrations and silently drops them before grouping by timepoint. Per-timepoint means, variances, and subject counts naturally reflect only the available data — no changes needed downstream in `sparse_mean()` or `var_sparse_auc()`.

If all subjects at a given timepoint have `NA` concentrations, that timepoint is dropped from the mean profile.

## Tests added

- `as_sparse_pk` correctly drops NA rows and preserves the rest
- `pk.calc.sparse_auc` produces the expected AUC with the dataset from the discussion

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eff79252de1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.