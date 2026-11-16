# Issue

**Title:** Interval support functions: add/remove params and imputation

## Description

Supersedes #384, building on Gero1999's branch (their 50 commits are preserved
underneath). .

## Approach

The wide intervals data.frame carries one logical column per parameter and a
single `impute` value per row, so a change applying to only some parameters has
to split the row. #384 did that in place, which needed a fractional index column
to interleave clones, a pass to blank non-target parameters, and a cleanup pass
to drop rows left with nothing.

Converting to one row per interval and parameter, editing with ordinary
filtering, and converting back does the same work without that machinery.
Splitting and merging fall out of the conversion: parameters land in the same
row when every other value matches, and in different rows when they do not.

## Defects fixed

**Row splitting produced unusable objects.** `interval_add_impute()` with
`target_params` left `NA` in the parameter columns of rows that no longer
calculate them:

```
check.interval.specification(): ERROR: Invalid value(s) in column auclast:NA
pk.nca():                       ERROR: ... missing value where TRUE/FALSE needed
```

`pk.calc.all.R` does `if (as.logical(interval[[n]]) & ...)`, which evaluates
`if (NA)` for any parameter with a calculation function. The existing tests
missed it because they set `data$intervals` directly and never re-validated or
calculated. Parameter columns are now `FALSE`, with regression tests that run
`check.interval.specification()`, `assert_intervals()`, and `pk.nca()` on a
split result.

**Multi-column `target_groups` matched the wrong rows.** The comparison
flattened the selected columns column-major and matched elementwise, ORing
across columns and returning a vector longer than `nrow(data)`:

```
data:   analyte = A1 A2 A1 A2 / route = iv iv ev ev
target: analyte = A1, route = ev
  was:  TRUE FALSE TRUE FALSE FALSE FALSE TRUE TRUE   (length 8)
  now:  FALSE FALSE TRUE FALSE
```

Single-column matching was correct, which is why the suite was green.

## Also

- `interval_add_param()` / `interval_remove_param()` with `param` and
  `param_pattern`, completing the set from #379. They share the same conversion.
- `assert_param_name()`, ported from #439 (which can now be closed — its
  `R/interval_model.R` does not parse, and its name-composition approach is
  superseded).
- Typed `pknca_error_*` / `pknca_warning_*` conditions throughout.
- `checkmate::assert_subset()` replaces a hand-rolled copy.
- NEWS entry corrected (it named `intervals_add_impute()`).

Tests: 80 in `test-intervals_support.R`; full suite passes.

## Note for review

The base branch is 607 commits behind `origin/main`. The first commit is a
standalone roxygen2 regeneration so the second commit's diff is only real
changes. Merging `origin/main` in is probably the next step before this is
mergeable.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a0da135639c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.