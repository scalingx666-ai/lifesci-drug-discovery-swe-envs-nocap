# Issue

**Title:** impute = NA, NULL, or an empty method string means no imputation

## Description

`PKNCAdata(..., impute = NA)` stored no imputation setting, so `pk.nca()` stopped with "Assertion on 'impute' failed: Must be of type 'atomic scalar', not 'NULL'". `impute = NULL` stopped in `PKNCAdata()`, and `impute = ""` (or an empty string in an imputation column) stopped in `pk.nca()` with `could not find function "NA"`. A leading separator (`" start_conc0"`) made an empty method name that was not found, and `interval_add_impute()`/`interval_remove_impute()` wrote such strings back with a leading comma.

```r
d <- data.frame(time = 0:4, conc = c(0, 4, 3, 2, 1))
o <- PKNCAdata(PKNCAconc(d, conc ~ time), PKNCAdose(data.frame(time = 0, dose = 1), dose ~ time),
               impute = NA, intervals = data.frame(start = 0, end = 4, auclast = TRUE))
pk.nca(o)
```

## Fix
- `PKNCAdata()` stores `NA_character_` for `NA` and `NULL`: the "impute" column of the intervals when there is one, else no imputation. `pk.nca()` reads a `NULL` setting the same way.
- `pk.nca.interval()` decides whether to impute from the parsed method list, so a string with no method names means no imputation.
- `PKNCA_impute_fun_list()` and `impute_split()` drop the empty name a leading separator splits off.

## Tests
- `NA`, `NA_character_`, and `NULL`, with and without an "impute" column, against the unimputed result.
- `""`, `" "`, and `" , "` as the argument and as an interval column, next to an interval that does impute (exact AUC).
- A `PKNCAdata` object with `$impute <- NULL`.
- `add_impute_method()`/`remove_impute_method()` with leading and trailing separators (exact strings).

Stacked on `fix/interp-iv-bolus-warning`; this PR's diff is only this fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96fe56700855`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.