# Issue

**Title:** fix: check exclusion thresholds with assert_number(), not testthat

## Description

exclude_nca_by_param() validated min_thr and max_thr with checkmate::expect_number(), which is a testthat expectation:  it loaded testthat ("Loading required namespace: testthat") and failed where testthat is not installed, which reached pknca_exclude_rules() and every exclude_nca_*() rule.  It now uses checkmate::assert_number(), so a bad threshold is an ordinary checkmate error.  A test runs the rules in a fresh R session with the installed package and checks that testthat stays unloaded (skipped under load_all()), and another checks the error is not a testthat expectation.

Version is 0.12.1.9001, so downstream pins can tell this from the development version before the date-time and exclusion-rule work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6797c80bbb69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.