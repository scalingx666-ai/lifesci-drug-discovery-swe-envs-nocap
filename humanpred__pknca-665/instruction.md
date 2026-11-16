# Issue

**Title:** Use the concentration time unit when detecting the dosing interval

## Description

## Summary
- `PKNCAdata()` and `pk.nca()` now pass the time unit of the concentration data, the `timeu` given to `PKNCAconc()` as a value or a column, to `find.tau()`, so the detected dosing interval is matched to the nominal intervals from `find.dose.regimen()`.
- New trailing `timeu` arguments on `choose.auc.intervals()` and `pk.nca.interval()`, and on the internal `resolve_dose_tau()`.
- Data without a time unit, with rows giving more than one unit, or with a unit that cannot be converted to hours, are unchanged. Date-time data without a time unit, which PKNCA converts to hours, are matched to the nominal intervals in hours.
- A time unit column may also be a grouping column.
- Dose regimen warnings name their group and are given once per group, instead of once per subject and interval. They share the parent class `pknca_warning_dose_regimen`, and they are kept when interval generation then errors. `PKNCAdata()` warnings no longer name the internal `data_intervals` column in their group prefix.

## Behaviour changes
- With a time unit, dose times recorded a little early or late give the nominal interval: doses at 0, 24.5, 49, 73 and 97.5 h give tau 24 rather than 24.5. The steady-state interval after the last dose and multiple-dose parameters such as `mrt.md.obs` change accordingly.
- With a time unit, an interval that matches no nominal interval, such as dosing every hour, gives `pknca_warning_tau_not_nominal` where it was silent.
- Without the units package, only a unit of `"hr"` enables nominal matching; other units fall back to the intervals found in the data, as documented in `find.dose.regimen()`.

## Tests
- New tests in test-choose-intervals.R and test-pk.calc.all.R, including the unit as a grouping column, sparse data, hourly dosing through `pk.nca()`, and date-time data without a unit. One legacy single-dose test in test-class-PKNCAdata.R now expects the not-nominal warning for doses 60 minutes apart in minutes, and the IV mrt/vss test expects the undetermined-tau warning once per group.
- The full suite passes, and R CMD check gives 0 errors and 0 warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d7b31cd5b5f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.