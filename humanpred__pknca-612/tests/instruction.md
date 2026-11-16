# Issue

**Title:** Fix missing dose time imputed into AUCint, and stop asking for bug reports on user errors

## Description

## Missing value imputed for time

With no dosing data, `pk.nca()` supplies a sentinel dose row with `time = NA_real_`. The dose-aware interval parameters (`aucint.last.dose`, `aumcint.inf.pred.dose`, and the rest of the `*int.*.dose` family) map `time.dose` to that column, so `pk.calc.auxcint()` both added `NA` to the set of times to interpolate to and handed `NA` to `interp.extrap.conc.dose()` as a dose to place on the timeline. The `NA` reached `assert_time()` and aborted the entire `pk.nca()` run:

```
Error with interval start=0, end=Inf: Assertion on 'time' failed: Contains missing values (element 1).
```

`pk.calc.auxcint()` now guards `time.dose` the way `pk.calc.c0()` already does — same `pknca_warning_timedose_na` class, same `exclude` idiom — so each dose-aware parameter reports `NA` with `exclude = "dose time is missing"`, matching the message `pk.nca()` already emits about missing dosing information. The dose-unaware siblings still calculate.

## "Please report a bug."

`pk.nca.intervals()` prefixed that to every error from an interval calculation, including ones PKNCA raised itself to say what the user has to change. Requesting `time_above`, `f`, or `mrt.md.obs` without the interval column each needs reported a bug rather than the missing column.

The prefix is now applied only to `pknca_error_internal_*` conditions and to unclassed errors from outside PKNCA. Two "should never happen" classes predating that convention are renamed into it so the split is mechanical. The missing-argument error also names the parameter and says to give the value as an interval column.

Both error sites were marked `# nocov` as unreachable; they are reachable, so those markers are removed and tests added.

## Not addressed

Running the issue's reprex verbatim still errors, on pre-existing intentional behavior rather than this bug:

- Missing `volume` errors naming `ae`, `fe`, `volpk`, `clr.*` — the behavior added in #194.
- `f`, `time_above`, `mrt.md.*`, `vss.md.*` need interval columns the user must supply (`dose1`/`dose2`, `conc_above`, `tau`) — the `non_pknca_covered_params` that the #473 test deliberately excludes. Their error message is now actionable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9858204b5a50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.