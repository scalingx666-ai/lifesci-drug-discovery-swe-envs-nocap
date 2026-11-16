# Issue

**Title:** missing PK parameters

## Description

add missing PK parameters across all AUC variants and extends IV and interval AUMC coverage.

## Changes

### `R/pk.calc.simple.R`
- Added 51 derived PK parameters covering:
  - 11 clearance parameters (`cl.*`)
  - 9 elimination rate constant parameters (`kel.*`)
  - 6 mean residence time parameters (`mrt.*`)
  - 3 IV mean residence time parameters (`mrt.iv.*`)
  - 9 volume of distribution at steady state parameters (`vss.*`)
  - 13 terminal volume of distribution parameters (`vz.*`)
- Sparse PK variants have been commented out and will be addressed in a separate pull request.

### `R/aucint.R`
- Introduced `pk.calc.auxcint()` as a combined internal wrapper mirroring the `pk.calc.auxc()` pattern used in `auc.R`
- Added `pk.calc.aumcint()` and AUMC interval variants: `aumcint.last`, `aumcint.last.dose`, `aumcint.all`, `aumcint.all.dose`, `aumcint.inf.obs`, `aumcint.inf.obs.dose`, `aumcint.inf.pred`, `aumcint.inf.pred.dose`
- Registered all `aumcint.*` parameters via `add.interval.col()` and `PKNCA.set.summary()`

### `R/auciv.R`
- Introduced `pk.calc.auxciv()` as a combined internal wrapper mirroring the `pk.calc.auxc()` pattern used in `auc.R`
- Added `pk.calc.aumciv()` and AUMC IV variants: `aumcivlast`, `aumcivall`, `aumcivint.last`, `aumcivint.all`, `aumcivinf.obs`, `aumcivinf.pred`
- Added `pk.calc.aumciv_pbext()` for percent back-extrapolated AUMC and registered all `aumcivpbext.*` parameters
- Registered all `aumciv.*` and `aumcivpbext.*` parameters via `add.interval.col()` and `PKNCA.set.summary()`

## Check Results
- `devtools::check()`: 0 errors ✔ | 0 warnings ✔ | 1 note
  - Note: timestamp verification — Windows environment issue, not code

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92628e101d83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.