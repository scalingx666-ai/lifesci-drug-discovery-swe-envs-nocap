# Issue

**Title:** Wire lloq from PKNCAconc through to the Tobit half-life method

## Description

## Problem

When `hl_method = "tobit"` is set via `PKNCAdata(options = list(hl_method = "tobit"))`,
the `lloq` value was not wired through to `pk.calc.half.life()`, so a full `pk.nca()`
run terminated with a generic "Please report a bug" error instead of computing the
half-life. There was no way to supply the lower limit of quantification that the Tobit
method requires. (Bug documented in the pknca-book `BUILDING_SETUP.md` "Known bug" section.)

## Fix

Add an `lloq` argument to `PKNCAconc()` — either the name of a column in the data
(per-observation LLOQ) or a numeric scalar applied to all observations — and thread it
through the calculation pipeline to `pk.calc.half.life()`, mirroring the existing
`volume` / `exclude_half.life` wiring:

- **`PKNCAconc()`** stores `lloq` via `setAttributeColumn()` with a numeric check.
- **`prepare_PKNCAconc()`** materializes the `lloq` column into the per-interval conc data.
- **`pk.nca.interval()`** maps `lloq` to the half-life function and keeps it aligned with
  `conc` when half-life points are manually included/excluded (a scalar is broadcast).

When `lloq` is omitted, behavior is unchanged (the column/attribute is not added).

## Docs & tests

- Replaced the non-working `eval = FALSE` "Full NCA workflow" example in the Tobit
  vignette with a runnable one using `PKNCAconc(..., lloq = ...)`.
- Added `NEWS.md` entry and regenerated `man/`.
- New tests: end-to-end `pk.nca()` Tobit runs (scalar lloq and per-observation column,
  both matched against a direct `pk.calc.half.life()` call) plus `PKNCAconc` construction
  and numeric-validation tests.

## Verification

- `devtools::test()`: PASS 2587, FAIL 0, ERROR 0
- `devtools::check()`: 0 errors, 0 warnings (2 pre-existing notes unrelated to this change)
- Tobit vignette knits and shows the half-life computed with BLQ points retained.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10457993ece0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.