# Issue

**Title:** feat: get the half-life fit and interpolate along it

## Description

.

Adds the two things requested in the issue, built on the parameters `pk.nca()` already produces.

### `get_halflife_fit()`

The log-linear half-life fit for each group and interval, as slope, intercept, and the time range of the concentrations used:

```r
o_conc <- PKNCAconc(Theoph, conc~Time|Subject)
o_data <- PKNCAdata(o_conc, intervals = data.frame(start = 0, end = Inf, half.life = TRUE))
get_halflife_fit(pk.nca(o_data))
#   Subject start end intercept       slope time_first time_last
# 1       6     0 Inf  2.033404 -0.08779574       2.03     23.85
# 2       7     0 Inf  2.288550 -0.08833650       6.98     24.22
```

The fit is reconstructed from `lambda.z`, `clast.pred`, and `tlast` rather than refit. Per the concern raised in the issue about anchoring on a point that may be excluded from the half-life: `clast.pred` is the *regression prediction* at `tlast`, not an observed value, so it lies on the line whether or not `tlast` was among the points used. The same holds for the Tobit path, where `clast.pred = exp(log_c0 - lambda_z*tlast)`.

### `get_halflife_curve()`

Concentrations along that line, following the defaults set out in the issue:

```r
# n equally-spaced times spanning the concentrations used for the fit
get_halflife_curve(o_nca, n = 50)
# specific times
get_halflife_curve(o_nca, tout = c(12, 24, 36))
```

- Concentrations, not log-concentrations
- `tout` / `n` mirror `xout` / `n` in `stats::approx()`
- Extrapolation later is on by default (`extrapolate_later = TRUE`)
- Extrapolation earlier is off by default (`extrapolate_earlier = FALSE`); such times give `NA`

With `n`, the times span the concentrations used for the fit, so `tout` is what extrapolates. The two flags gate the times you ask for rather than generating a range, which keeps them meaningful when the interval `end` is `Inf`.

### Times are on the concentration-data scale

Times in a `PKNCAresults` object are relative to the interval `start`. Both new functions shift them back onto the same scale as the times in the concentration data, so the fitted line can be drawn against the observed concentrations without the caller adjusting anything. This follows `get_halflife_points()`, which already aligns to the original concentration rows.

### Notes

- Both functions accept a `PKNCAresults` or a `PKNCAdata` object, as `get_halflife_points()` does. The interval-pruning in `get_halflife_points.PKNCAdata()` is factored into `halflife_only_PKNCAdata()` and shared.
- Excluded or uncalculable half-lives give an all-`NA` fit row rather than a dropped row, so the interval stays visible. A partially-available fit is `NA`'d out entirely rather than reported half-populated.
- The naming discussion in the issue landed on `get_halflife_curve()` to sit with `get_halflife_points()` and `get_halflife_fit()`.

### Testing

11 new tests. The strongest one refits from scratch — takes the points `get_halflife_points()` reports were used, runs `lm(log(conc) ~ Time)` on the unshifted times, and compares against the reported fit on an interval with `start = 5`, which is what actually pins the time-shift arithmetic. Agreement is to machine precision (max absolute difference 2.2e-15 for intercept, 1.4e-16 for slope). Also covered: exact expected values, multiple intervals per group, exclusions, units, both extrapolation gates, and argument validation.

Full suite passes (3493 tests). `vignette("v07-post-processing")` gains sections for both functions and renders cleanly.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9858204b5a50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.