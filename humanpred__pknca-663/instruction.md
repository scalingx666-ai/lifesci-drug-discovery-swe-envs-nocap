# Issue

**Title:** feat: add max.hl.points and min.hl.start.time half-life options

## Description

Adds the two "Lambda Z Rules for Best Fit" of Phoenix WinNonlin as PKNCA options
and `pk.calc.half.life()` arguments:

- **`max.hl.points`**: the most points automatic half-life point selection may
  use.  Defaults to `Inf` (no limit).  It must be more than `min.hl.points`
  (checked when the half-life is calculated, so it holds however the two are
  given; `pknca_error_max_hl_points_not_above_min`), and as an option it must be
  at least 3.  A non-integer is rounded with a warning, as for `min.hl.points`.
- **`min.hl.start.time`**: the earliest time a fit may start.  Defaults to 0,
  which does not restrict the points (even for negative times); it must be a
  single finite nonnegative number.  Within `pk.nca()` it is the time since the
  start of the interval.

Every candidate span ends at the last point, so the start time removes the
points before it and the maximum shortens the span search.  Both apply to the
log-linear and Tobit methods (for Tobit, `max.hl.points` counts above-LLOQ
points, as `min.hl.points` does) and are ignored for manually selected points.
A too-few-points exclusion says when the start time removed points.

Defaults leave every existing result unchanged.

Tests pin exact results: with an exact exponential every span fits perfectly,
so selection takes the most points allowed, and each rule's result must equal a
manual fit to the points it allows (and, for Tobit, the fit of the data trimmed
to the same windows).  Also covered: the max/min check, the default of 0 with
negative times, the too-few-points message, option validation, and options
passed through `PKNCAdata()` to `pk.nca()`.  The half-life vignette lists the two
rules with an example.

`devtools::test()`: 0 failures (6197 passing).  `R CMD check` (vignettes
skipped): 0 errors, 0 warnings, 1 note (the worktree's `.git`).  The edited
vignette was rendered separately.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ca4fe23586d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.