# Issue

**Title:** feat: PPGRPID in the CDISC output from caller-named grouping columns

## Description

## Summary

- `as.data.frame(results, out_format = "cdisc")` now has a `PPGRPID` column (last, after `PPTPTREF`/`PPRFTDTC`): `"<prefix1><value1>.<prefix2><value2>.I<nn>"`, e.g. `"A.P1.I01"`, `"P2.I01"`, or `"I01"`.
- New `grpid_cols` argument (named character vector: PKNCAconc grouping column to the text written before its value, in prefix order; not the subject or analyte) on `as.data.frame()` and `PKNCAdata()`. The `PKNCAdata()` value is the default; the `as.data.frame()` value overrides it; `character()` forces an interval-only id.
- New `grpid_numeric` argument on `as.data.frame()` and `PKNCAdata()` (the default): columns written as whole numbers >= 1 (`"01"` becomes `1`).
- Intervals are numbered densely from 1 by numeric start then end within each combination of the subject, analyte and `grpid_cols` columns; other grouping columns do not enter PPGRPID; an interval without result rows has no number; records of one interval share the number; no `interval_id` is needed. The number has at least two digits and as many as the largest interval number needs, so text order is time order. Numbers and width come from all intervals of the results, so filters never renumber, and value checks run over all results.
- Classed errors (`pknca_error_grpid_*`) naming the column, prefix or values for: subject/analyte/non-group columns, malformed arguments, empty or `.`-containing values or prefixes, distinct values rendering alike, non-whole-number numeric values, and a missing interval start or end.

## Test plan

- [x] `tests/testthat/test-cdisc-grpid.R`: no grpid columns, one and two prefixed columns, prefix order, numeric rule and its errors, separator/empty/collision errors through `as.data.frame()`, padding at 99 and 100 intervals with only the last three returned, shared numbers within an interval, a grouping column left out of `grpid_cols`, intervals without result rows, zero-row output, two subjects, sparse results, excluded rows, factor and NA values, `PKNCAdata()` defaults overridden.
- [x] Full `rtest.sh test`: 0 failures. `rtest.sh check`: 0 errors, 0 warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc14f707f7b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.