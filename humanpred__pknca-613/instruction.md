# Issue

**Title:** Test imputation methods with degenerate data; fix start_predose with missing times and concentrations

## Description

Adds the three degenerate-input scenarios from the issue — all concentrations `NA`, all times `NA`, all concentrations 0 — to each of the four imputation methods. Three of the four already behaved sensibly; `start_predose` did not, in two separate ways.

## Bug 1: missing times crashed `start_predose`

`time.group < start` yields `NA` when a time is missing, and `if (any(mask_predose))` cannot branch on that, so the method stopped with:

```
missing value where TRUE/FALSE needed
```

A measurement at an unknown time cannot be known to be predose, so it is now excluded from selection. Two adjacent latent problems in the same function are fixed alongside it: `time.group == time_predose` would pull spurious `NA`-time rows in next to the real predose sample (now `%in%`), and the automatic `max_shift` for `end = Inf` used `max(time)`, which is `NA` if any time is missing.

No behavior change when times are complete.

## Bug 2: `start_predose` shifted missing concentrations

A missing predose value carries no information, but it was still shifted to the interval start, adding a missing concentration where there had been no measurement at all.

This reached real analyses. NA cleaning happens inside the individual parameter calculations rather than before imputation, so missing concentrations do arrive at the imputation functions during a live `pk.nca()` run. With `conc.na = 0`, the shifted `NA` became a *measured zero* at the start time and `auclast` was reported as `51.17835` — computed from a measurement that was never taken. It is now missing, matching the un-imputed result.

The predose sample is still selected by time, so a missing value at the nearest predose time skips the shift rather than reaching further back to an older sample.

## Tests

One block per method pinning all three scenarios, plus mixed cases where a missing time or concentration sits alongside usable data:

| Method | All conc `NA` | All times `NA` | All conc 0 |
|---|---|---|---|
| `start_conc0` | start set to 0, `NA`s untouched | start row added, unknown times sort last | no-op / zero row added |
| `start_cmin` | no minimum exists → unchanged | nothing known in-interval → unchanged | 0 imputed at start |
| `start_predose` | not shifted (was: `NA` shifted) | unchanged (was: an error) | 0 shifted |
| `end_conc_drop` | end row still dropped | nothing known at end → unchanged | end row still dropped |

Plus an end-to-end test through `pk.nca()` pinning the `conc.na = 0` case above, since that is where the fabricated value was user-visible.

## Docs

The second fix is a behavior change rather than only a crash fix, so it gets its own `NEWS.md` entry. Also updated: the `@describeIn` text, the regenerated `man/PKNCA_impute_method.Rd`, and the `start_predose` bullet in `vignettes/v08-data-imputation.Rmd`.

Regeneration produced the usual unrelated drift (the hand-maintained `S3method(AIC,list)` line and the two dplyr-inherited pages, whose `@inheritParams` text comes from a newer installed dplyr). Those three are reverted; only the impute page is included.

## Verification

Full suite: `FAIL 0 | WARN 2 | SKIP 0 | PASS 3447`. Both warnings are pre-existing and in the `tss` code. `spelling::spell_check_package()` flags nothing new.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13c1d3215108`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.