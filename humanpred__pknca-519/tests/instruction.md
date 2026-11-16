# Issue

**Title:** Refactor normalize.data.frame — Fix Deprecation Warning & Improve Robustness

## Description

Summary

This PR refactors normalize.data.frame to fix a dplyr deprecation warning for ungrouped data, improve join strategy, and align the codebase to a consistent dplyr style.

Problem
When calling normalize() with ungrouped data (no common group columns between object and norm_table), the following deprecation warning was triggered: Warning: Using `by = character()` to perform a cross join was deprecated in dplyr 1.1.0. Please use `cross_join()` instead.
This was caused by anti_join(by = character(0)) and merge(by = character(0)) being called without guarding against the ungrouped case.

Changes
Fix ungrouped data handling & full dplyr style consistency •	Wrapped anti_join missing-groups check inside if (length(common_colnames) > 0) to avoid deprecated cross join path •	Added else branch with nrow(norm_table) != 1 guard for ungrouped duplicate check — enforces exactly one row •	Replaced merge(by = character(0)) with dplyr::cross_join() for ungrouped join •	Replaced `merge()` with `dplyr::inner_join()` for grouped join — preserves left-table row order unlike `merge()`. Row count is equivalent to `merge()` here since missing groups are already validated before the join, guaranteeing all rows will match. •	Replaced base R [ filtering with dplyr::filter() •	Replaced base R $ assignments with dplyr::mutate() blocks •	Replaced df[, colnames(object)] with dplyr::select(all_of(names(object))) for cleaner column reordering

[ FAIL 0 | WARN 3 | SKIP 0 | PASS 2237 ]
Warning (test-PKNCA.options.R:440:3): PKNCA.set.summary input checking `reset = TRUE` is not intended for general use, summary() may not work after resetting summary instructions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f37b68cc840`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.