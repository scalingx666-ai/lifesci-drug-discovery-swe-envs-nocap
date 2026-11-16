# Issue

**Title:** Speed up the pk.nca() calculation engine

## Description

Implements items 1, 2, 3, 4, and 6 of `design/performance-optimization-plan.md` (item 5, assert-once validation, stays its own later PR), plus the argument-source-map restructure, the `lambda.z.corrxy` type fix, and a result-shape check.

**What changed** (one commit per item):

- Imputation methods resolve via `exists()` from the namespace outward instead of `utils::getAnywhere()` scanning the whole search path (item 1).
- Each parameter's prepared argument list and required-formals set are cached on its registry entry; re-registering a parameter replaces the whole entry, so the cache cannot go stale (item 6).
- Each interval iterates only the parameters it requests instead of every registered one (item 4).
- `fit_half_life()` returns a named list instead of a one-row data.frame; the Tobit path keeps data.frames because its candidates are `rbind()`ed and `optim()` dominates there (item 3).
- Interval results accumulate as vectors and become one data.frame per interval instead of one per parameter (item 2).
- The 22-branch argument-resolution ladder is now a per-interval source map plus a computed-values store that grows as the interval's calculations proceed, carrying exclusions along with the values. This is readability work more than speed and is a separately revertible commit.

**Behavior changes** (each in NEWS):

- `lambda.z.corrxy` is `NA_real_` instead of a logical `NA` when the correlation cannot be computed, so the column type no longer depends on the number of fit points.
- A calculation function registered with `add.interval.col()` whose returned names and values do not pair up now stops with an error naming the function and both lengths. Previously a zero-row data.frame return gave an obscure error, and a multi-row return silently reported values under the wrong parameter names.

**Verification**

- The full `as.data.frame(pk.nca(...))` of the plan's three benchmark workloads, and `summary()` of workload A, are `identical()` to their pre-change values after every commit — never weakened to `all.equal()`.
- Test suite: 0 failures (the 2 warnings are the pre-existing Tobit non-convergence). `R CMD check`: no ERRORs or WARNINGs, 2 pre-existing NOTEs.
- Timings (minimum of 3 reps, before → after; the ratios are the claim, the seconds are machine-noisy): workload A 20.3 → 7.8 s (0.38×), B 10.4 → 6.3 s (0.61×), C 4.3 → 2.8 s (0.65×). Per-item numbers and caveats are in the plan's "As implemented" section.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0fb884b4d57d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.