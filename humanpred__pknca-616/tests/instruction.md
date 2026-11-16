# Issue

**Title:** Calculate IV bolus AU(M)C without a time 0 concentration

## Description

.

## The problem

With an IV bolus and no sample at time 0, every `auciv`/`aumciv` parameter came back `NA`:

```r
d_iv <- data.frame(conc = c(4, 2, 1, 0.45), time = c(5, 15, 30, 60))
o_conc <- PKNCAconc(d_iv, conc~time)
o_dose <- PKNCAdose(data.frame(dose = 100, time = 0), dose~time, route = "intravascular")
o_nca <- pk.nca(PKNCAdata(o_conc, o_dose, intervals = data.frame(start = 0, end = Inf, aucivinf.obs = TRUE)))
#>  aucinf.obs           NA   Requesting an AUC range starting (0) before the first measurement (5)...
#>  aucivinf.obs         NA   Requesting an AUC range starting (0) before the first measurement (5)...
```

`c0` back-extrapolates fine (5.657 by logslope), but `pk.calc.auxciv()` corrects an already-calculated AUC, and an AUC may not start before the first measurement — so there was nothing to correct.

## The fix

`c0` *is* the concentration at time 0, so the IV AUC is calculable even though the plain AUC is not. `pk.calc.auxciv()` now branches three ways:

| At time 0 | Behavior |
|---|---|
| A concentration is measured | Unchanged correction path — no existing number moves |
| No concentration, `auxc` calculated | `auxc` came from the `aucint` family, which extrapolates back with `conc.origin` (zero); that segment is swapped for the `c0` one |
| No concentration, `auxc` is `NA` | Recompute on the `c0`-augmented profile via `fun_auxc` / `auc.type` |

The recomputed value is marked `"DO NOT EXCLUDE"` so the base parameter's exclusion reason does not suppress a value it did not produce.

Result:

```
 aucinf.obs           NA      Requesting an AUC range starting (0) before...
 aucivinf.obs        109.03   <NA>
 aucivpbextinf.obs    NA      Requesting an AUC range starting (0) before...
```

The percent back-extrapolated is `NA` because the AUC *without* back-extrapolation is what is missing — that is the quantity it is a percentage of.

## `formalsmap` constants

All six AUC variants share `FUN = "pk.calc.auciv"` and differ only in `formalsmap$auc`, so at the recompute point the function could not tell `aucivlast` from `aucivall`. `lambda.z`/`clast` separate the `.inf` variants, but `last` vs `all` needed a literal.

`add.interval.col()` now accepts an `I()`-wrapped `formalsmap` value, passed to the calculation function as a constant rather than resolved as a data source or parameter name:

```r
formalsmap = list(auc = "aucall", auc.type = I("AUCall"), lambda.z = NULL, clast = NULL)
```

`parameter_direct_refs()` filters these out so a constant is never mistaken for a dependency. This keeps the recompute logic at a single point instead of needing twelve wrapper functions.

## Incidental bug fix

The time 0 check tested the **raw** times while computing on the BLQ/NA-cleaned data. An `NA` concentration at time 0 satisfied `0 %in% time`, then indexed past the cleaned data — so the correction was computed from the wrong two points and raised three spurious "Requesting an AUC range starting (0)..." warnings. The `#353` test asserted all three; it now asserts one and pins `aucivinf.obs`.

## Two things worth a look

- **`aucivpbextint.last` / `aucivpbextint.all` are not `NA`** — they come out at 14.626, matching the measured-zero case. `aucint.*` defines an AUC from time 0 via `conc.origin = 0`, so the back-extrapolated fraction is well-defined there. Only the four non-`int` percentages are `NA`. Easy to change if `NA` is preferred for consistency.
- **Both `pk.calc.auciv()` and `pk.calc.aumciv()` gained arguments** (`auc.type`, `lambda.z`, `clast`), inserted before `...`. Positional callers past `auc`/`aumc` would be affected; named callers are not.

## Verification

- New tests pin all 12 IV AU(M)C values, and assert they are **identical** to the same profile with a measured zero at time 0 — the two code paths must agree.
- `aucivlast = 95.061` checked by hand: 23.904 (0→5 from `c0`) + 28.854 + 21.640 + 20.663; `aucivinf.obs` adds 0.45/λ<sub>z</sub> = 13.969.
- A test covers the new `I()` `formalsmap` constant end to end, including that it does not appear in `get.parameter.deps(recursive = TRUE)`.
- Full suite: 3453 tests, 0 failures. `R CMD check`: 0 errors, 0 warnings, 1 note (the `.git` directory, from checking a worktree in place).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ddf32af94985`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.