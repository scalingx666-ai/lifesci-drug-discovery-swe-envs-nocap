# Issue

**Title:** Add end_conc_drop imputation method

## Description

Adds `PKNCA_impute_method_end_conc_drop()`, which removes a concentration sitting exactly at `time == end` for an interval (no-op if none is present).

Because it works through the `impute` column, it's per-interval: drop the boundary point only on profiles where it belongs to the next dose (e.g. an imputed C0), while leaving genuine troughs untouched.

```r
intervals <- data.frame(
  start  = c(0, 24), end = c(24, 48), tmax = TRUE,
  impute = c("end_conc_drop", NA)   # interval 1 only
)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eff79252de1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.