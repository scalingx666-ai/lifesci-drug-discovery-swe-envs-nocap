# Issue

**Title:** Test superposition interpolation/extrapolation methods, and validate them

## Description

`superposition()` passes `method` and `auc.type` through to `interp.extrap.conc()`, but no test exercised anything other than the default `"lin up/log down"`, and `auc.type = "AUCall"` was untested entirely.

**Tests** are built on one profile — `conc = c(0, 4, 2, 8, 4, 2, 1, 0)`, `time = 0:7` — with a dip before tmax (separates `lin-log` from `lin up/log down`), an exactly log-linear tail so λz = log 2 makes extrapolation hand-computable, and a trailing BLQ (separates `AUCall` from `AUClast`):

- each `method`, checked with `tau = 4, n.tau = 2` so the method must apply in both dosing intervals
- each `auc.type`, checked at three times after tlast; plus `AUCall` collapsing to `AUClast` when no BLQ follows tlast
- the `auc.method` option, and an explicit `method=` overriding it
- both arguments surviving the `superposition.PKNCAconc()` `...` → `mclapply()` path

**Validation:** `method` and `auc.type` were only checked where they were used, so an invalid value was silently ignored when `tau*n.tau <= tlast` or when all concentrations were zero. They are now checked with the other inputs. Note that this makes `auc.type` case-sensitive in `superposition()`, matching `choose_interval_method()` and `pk.calc.auxc()`; `extrapolate.conc()`'s `tolower()` previously accepted e.g. `"aucinf"`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c217f0628d51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.