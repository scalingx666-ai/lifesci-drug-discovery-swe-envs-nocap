# Issue

**Title:** ci: run the R 4.1 job with the suggested packages its tests use

## Description

The R 4.1 job installed only the hard dependencies, so 80 of its tests skipped: 44 for units, 22 for lme4, 11 for emmeans, and 2 for cdiscdata, plus 1 MASS test that skipped on every R before 4.4.  Of those packages only lme4 and lmerTest cannot install there from current CRAN, and only because their dependencies Matrix (>= 1.7-0) and MASS (>= 7.3-60.1) need R 4.4 and pak installs only the newest release of a dependency; lme4 2.0-6 itself needs R >= 3.6 and Matrix >= 1.5-0.

The job now installs units, emmeans, lme4, lmerTest, and cdiscdata with Matrix pinned to 1.6-5 and MASS to 7.3-60.0.1, the last releases that support R 4.1.  ggtibble (R >= 4.3) is used only by a vignette, so the job still skips the vignettes with _R_CHECK_FORCE_SUGGESTS_ off.

The steady-state confint() test skips before R 4.4 only when MASS is missing; MASS is a recommended package and is installed with R.

Checked on R 4.1.3 (rocker/r-ver:4.1.3) with the dependencies resolved as r-lib/actions/setup-r-dependencies does (pak lockfile, empty library, no upgrades): R CMD check gives 0 errors and 0 warnings, and the tests give 7486 passed, 0 failed, and 3 skipped (the tests that need the package source, which skip in every R CMD check job).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6b5f0563813`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.