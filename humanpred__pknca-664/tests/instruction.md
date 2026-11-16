# Issue

**Title:** feat: summarize sparse AUClast as the mean with its standard error

## Description

A sparse AUClast is one estimate per group, with its standard error on a
different result row (`auclast_se`).  `summary()` showed the estimate alone and
described it as a geometric mean with a geometric coefficient of variation.

This lets the summary of one parameter take its spread from another parameter's
results, without restructuring `summary.PKNCAresults()`:

- `PKNCA.set.summary()` gains `spread_for`.  The summary instructions of a
  parameter such as `auclast_se` name the parameter it gives the spread of
  (`spread_for = "auclast"`).
- Where a summary cell has results for `auclast_se`, `auclast` is summarized
  with `auclast_se`'s instructions:  `point()` on the AUC values, `spread()` on
  the standard errors, and its description ("arithmetic mean and standard
  error") in the caption.  The spread is computed for a single estimate too,
  since a sparse cell usually holds one.
- `auclast_se` gets no summary column of its own (also when requested in the
  intervals).  Cells without standard-error results, such as dense data, keep
  the parameter's own summary, and a column that mixes both is described by
  both in the caption.

`auclast_se`, `aumclast_se`, and the deprecated `sparse_auc_se` and `sparse_aumc_se` are registered this way. A summary row with more than one of these results is the `pknca_error_summary_multiple_spread` error, since each standard error describes one estimate. That happens if `drop_group` removes the group that separates them, or if intervals with the same start and end aren't told apart by a kept interval column.

Example (two treatments, sparse sampling):

```
 start end treatment     auclast cmax
     0  24         A 55.8 [3.30] 7.06
     0  24         B 49.7 [2.35] 7.30

Caption: auclast: arithmetic mean and standard error; cmax: geometric mean and geometric coefficient of variation
```

Tests pin each cell exactly against the run's own `auclast`/`auclast_se`
results:  one estimate per cell, two estimates combined with `drop_group`, no
column for a requested SE, an excluded SE (`[NC]`), the deprecated
`sparse_auclast`, the mixed-description caption, `spread_for` validation, and
`business.se_mean()`.  The sparse vignette notes the new summary form.

`devtools::test()`: 0 failures (6220 passing).  `R CMD check` (vignettes
skipped): 0 errors, 0 warnings, 1 note (the worktree's `.git`).  The sparse
vignette was rendered separately with this branch.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00e1db246444`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.