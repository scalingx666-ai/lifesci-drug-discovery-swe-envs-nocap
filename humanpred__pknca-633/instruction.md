# Issue

**Title:** feat: allow half-life point selection on unadjusted r-squared

## Description

`pk.calc.half.life()` gains an `r.squared.factor` argument and PKNCA gains a matching option, so the terminal-phase window can be selected on the unadjusted r-squared rather than the adjusted one. Set `r.squared.factor` to the allowance and `adj.r.squared.factor` to `NA`; exactly one of the two must be `NA`. **The default is unchanged.**

```r
# Theophylline subject 6
pk.calc.half.life(conc, time)
#> lambda.z.n.points = 7, half.life = 7.895   (adjusted r-squared, default)

pk.calc.half.life(conc, time, adj.r.squared.factor = NA, r.squared.factor = 0.0001)
#> lambda.z.n.points = 3, half.life = 7.569   (unadjusted r-squared)
```

This follows the 7-point implementation sketch in the issue thread.

### Implementation

- `check_r_squared_factor_option()` (one new internal helper) validates both options, deriving its wording, default, error class, and warning class from the option name. `adj.r.squared.factor` keeps every message and condition class it had; both options now accept `NA`.
- `pk.calc.half.life()` resolves both factors through `PKNCA.choose.option()`, aborts with class `pknca_error_r_squared_factor_choice` when both are `NA` or both are non-`NA`, and drives the selection comparison and the no-surviving-span exclusion reason from whichever r-squared is in use.
- The pair is checked only for automatic selection, matching the documented behaviour that both factors are ignored when `manually.selected.points = TRUE`.

`na.ok = TRUE` on the `assert_number()` call is load-bearing, not defensive: `pk.nca()` merges the complete default option list into `data$options`, so `PKNCA.choose.option()` re-validates the `NA` default on every run.

### Two decisions worth a look

- **`min.hl.points = 2` under r-squared selection always picks the 2-point fit**, since a 2-point fit has an r-squared of exactly 1. That is the criterion behaving as defined rather than a fault, so it is documented in `@param` and pinned by a test rather than warned about.
- **Setting one option without the other is accepted where options are set and then fails at calculation time.** `PKNCAdata()` and `PKNCA.options()` validate one option at a time, so the pair can only be checked where it is used. The error is classed and says what to do, and `NEWS.md` plus the vignette both say to set them together. A cross-check in `PKNCAdata()` would move the failure earlier if you would prefer that.

### Docs

`NEWS.md`; the regenerated `man/pk.calc.half.life.Rd`; the selection rule in `v06-half-life-calculation.Rmd` reworded around "the selection statistic" so the default and the alternative read as one rule; `v06-half-life-calculation-tobit.Rmd` (which restates the rule, and now says neither factor applies to `hl_method = "tobit"`); `v30-training-session.Rmd`; and the option table in `design/01-architecture.md`. The options vignette picks the new option up automatically from `.PKNCA.option.check`.

The `v06` decision-tree figure names the automatic-selection options from a single vector guarded by `stopifnot()`; the fourth name overflowed the box, so the label now wraps across two lines and the "three options at left are ignored" count is computed.

### Testing

`devtools::check()`: 0 errors, 0 warnings, 2 NOTEs — both pre-existing (a `.git` directory because this was checked from a worktree, and the existing spelling wordlist drift). Full suite passes; vignettes rebuild.

New tests cover the selection difference on Theophylline subject 6, the `options=` and global `PKNCA.options()` routes, end-to-end through `pk.nca()`, both mutual-exclusivity error cases, Tobit and manual selection being unaffected, the one-sided-option failure, the `min.hl.points = 2` degeneracy, and the reworded exclusion reason.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72cb50b37469`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.