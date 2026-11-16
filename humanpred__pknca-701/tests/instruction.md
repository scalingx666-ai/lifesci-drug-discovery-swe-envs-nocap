# Issue

**Title:** Warn when an interval requests parameters calculated on different AUC bases

## Description

An interval specification can request parameters that are not calculated on the same basis. For example, `aucint.all` (an interval AUC with AUCall) with `cav` (from AUClast), or `cl.obs` (AUCinf,obs) with `vz.pred` (AUCinf,pred). Such results look comparable but describe different things. This PR adds one classed warning, `pknca_warning_interval_inconsistent_parameters`, for those intervals.

## What is checked

- **AUC basis.** Every parameter calculated from AUCs is placed on the AUC bases that `pknca_interval_table()` builds intervals on:
  - dosing: single-dose AUCs or interval AUCs;
  - AUClast or AUCall;
  - AUCinf,obs or AUCinf,pred.

  A pair of parameters that no basis holds together is reported. The bases are built from the registry and cached in `.PKNCAEnv`. The cache is dropped when the registry changes, so a newly registered parameter is judged with no further code.
- **Secondary parameters** (`f.*`, `ratio.*`) and renal clearance (`clr.*`), which name their AUC with `pknca_ref()`, are judged by the AUC they reference.
- **Finite end.** A parameter that needs a finite interval end (an average concentration and the parameters calculated from one, or a parameter that applies only to repeated dosing) is reported when its interval ends at infinity.

## What is deliberately not judged

- **AUC reports against each other.** The AUCs, AUMCs and percent extrapolated are not judged against each other, and are not judged against other parameters on AUCinf,obs vs AUCinf,pred. Reporting both is common.
- **Parameters calculated from no AUC** (Cmax, Ctrough, the swing).
- **Parameters that apply only to repeated dosing.** Their definitions combine bases, as `pknca_interval_table()` does.
- **Route and sample type.** One interval commonly covers both arms of a crossover, or both plasma and urine.

## Where it runs

The warning is given by `PKNCAdata()`, `set_intervals()` and `pk.nca()`. Each gives one warning for the whole specification, not one per interval. Rows with the same parameters are judged together, and each problem is listed with the number of intervals it affects (at most 20 lines).

## Related changes

- `pknca_interval_table()` has a new `auc_type` argument: `"last"` (the default) or `"all"`.
- At an infinite end, `pknca_interval_table()` no longer offers parameters that need a finite end. Explicitly including one gives `pknca_warning_interval_include_finite_end`.
- The v01 and v30 vignettes use `aucall` where they had requested `aucint.inf.obs` alongside single-dose parameters.
- Knitted vignette figures that had been committed by accident are removed, and `vignettes/figure/` is ignored.

## Tests

- New `tests/testthat/test-interval-consistency.R`. It covers:
  - each rule, and the exact warning text;
  - the exemptions;
  - `pknca_ref()` parameters;
  - the cache being invalidated on registration;
  - one warning per call.
- Existing tests that request mixed bases on purpose now expect the warning.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9edefbe77afd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.