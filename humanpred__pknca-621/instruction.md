# Issue

**Title:** Fix aucint.inf.pred failing when the interval ends at infinity

## Description

.

`pk.calc.auxcint()` adds the concentration at `tlast` a second time when `clast.pred` differs from `clast.obs`, so that integration up to `tlast` uses the observed data and integration after `tlast` starts from the predicted concentration.

When the interval ends at infinity and no data point follows `tlast`, that duplicate is the last point in the interval. Extrapolation to infinity is analytic from `clast` and `tlast`, so the duplicate contributed only a zero-width interval — while making `tlast` occur twice in the time vector, so `choose_interval_method()` aborted with `tlast (8) must occur exactly once in time`.

The duplicate is now added only when a later point in the interval is actually integrated to from `clast.pred`.

## Verification

For the data in the issue, `aucint.inf.pred` is now 130.5668 against `aucint.inf.obs` of 131.0807. The difference is exactly `(clast.obs - clast.pred) / lambda.z`, and finite interval ends converge to it (`end = 24` gives 130.565; `end = 48`, `100`, and `500` all give 130.5668).

Tests cover the direct call for AUC and AUMC with a hand-derived expected value, the finite-end convergence, and the `pk.nca()` path from the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58a10b993a17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.