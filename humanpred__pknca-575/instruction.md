# Issue

**Title:** Regenerate documentation with roxygen2 8.0.0

## Description

Regenerates the four man pages that had drifted from roxygen2 8.0.0 output (the package already declares `Config/roxygen2/version: 8.0.0`; later PRs touched `man/` with older toolchains):

- `assert_number_between.Rd`, `assert_numeric_between.Rd`: `[any]` → `[\code{any}]`
- `filter.PKNCAresults.Rd`, `group_by.PKNCAresults.Rd`: `@inheritParams` text refreshed from dplyr 1.2.1, including `filter_out()`/`when_any()` references (links resolve against CRAN dplyr >= 1.2.0)

`NAMESPACE` and `DESCRIPTION` are unchanged. Docs-focused `R CMD check` (no tests/vignettes): 0 errors, 0 warnings.

Note: roxygen2 8 also flags `AIC.list` as needing `@export`/`@exportS3Method`; left out of this PR since fixing it changes `NAMESPACE` (separate follow-up).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29c2ac364408`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.