# Issue

**Title:** Realign include_half.life, exclude_half.life, and lloq after imputation

## Description

## Problem

When a profile has no sample at the interval start and imputation adds one (e.g. `PKNCAdata(..., impute = "start_conc0")`), `pk.nca.interval()` keeps the caller's original per-observation `include_half.life`, `exclude_half.life`, and `lloq` vectors. They are one element shorter than the imputed `conc`/`time`, so R recycles them in the half-life subset and each value applies to the observation *before* the intended one, without a warning.

```r
library(PKNCA)
t <- c(0.5, 1, 2, 4, 8, 12, 16, 24, 36, 48)
d <- data.frame(time = t, conc = round(10 * (exp(-0.03 * t) - exp(-t)) + 5 * exp(-0.2 * t), 4))
d$inc <- ifelse(d$time >= 24, TRUE, NA)   # intend: fit 24, 36, 48
iv <- data.frame(start = 0, end = Inf, half.life = TRUE, lambda.z.time.first = TRUE)
o <- PKNCAdata(PKNCAconc(d, conc ~ time, include_half.life = "inc"),
               PKNCAdose(data.frame(time = 0, dose = 100), dose ~ time),
               intervals = iv, impute = "start_conc0")
as.data.frame(pk.nca(o), out_format = "wide")$lambda.z.time.first
#> 16   (24 without imputation)
```

The same shift applies to `exclude_half.life` (excluding 48 h removes 36 h). With a per-observation `lloq` and `hl_method = "tobit"`, the calculation errors ("missing value where TRUE/FALSE needed").

This is common in practice: data where the pre-dose sample is at a negative time and is dropped before NCA, then imputed at the dose time.

## Fix

- `impute_conc_time()` now records, in an `"obs_index"` attribute, which original observation each imputed row came from (`NA` for an added one). It follows the observations step by step through the imputation chain: a step that adds or drops observations is followed by time; a step that keeps the number of observations is taken to modify them in place (so a user-defined method that shifts times still keeps the values with their observations). Chains such as `"start_conc0,end_conc_drop"` are handled.
- `pk.nca.interval()` uses it to realign `include_half.life`, `exclude_half.life`, and a per-observation `lloq`. Added observations are neither included nor excluded; they get a constant `lloq` (or `NA` when `lloq` varies, which is harmless for the built-in methods because Tobit drops observations at or before the end of the dose).
- **New error (proposed):** if an imputation step changes *both* the number of observations and their times (only possible with a user-defined method), the observations cannot be followed. Rather than silently dropping or misapplying the values, the half-life calculation raises `pknca_error_impute_obs_index` — only when it would actually use them (`include_half.life`/`exclude_half.life`, or a varying `lloq` with `hl_method = "tobit"`). Intervals without half-life, and log-linear half-life with a varying `lloq`, are unaffected. Happy to change this to a warning if you prefer.

Known limitation (documented in a comment): a user-defined step that drops one observation and adds another at the same time keeps the count unchanged and is indistinguishable from an in-place modification, so it is treated as in place. Fully covering that would need imputation methods to return observation identity.

## Tests

New tests in `test-pk.calc.all.R`:
- include/exclude flags and a per-observation `lloq` (Tobit) give the same half-life with and without `start_conc0` when there is no sample at the dose time;
- the `"start_conc0,end_conc_drop"` chain;
- a user-defined method that changes times in place;
- the new error, and that it is not raised when the half-life does not use the values.

The two existing `impute_conc_time()` expectations now include `obs_index`. The new tests fail on `main`; the full suite passes (1219 tests, 0 failures).

NEWS updated under Bug fixes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `665acfa8e7b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.