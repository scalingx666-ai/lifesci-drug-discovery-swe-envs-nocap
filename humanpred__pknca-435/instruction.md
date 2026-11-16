# Issue

**Title:** Allow non-unique units columns (PKNCAconc & PKNCAdose)

## Description

Makes `PKNCAdata$units` table able to include any group variable stratifying the units in PKNCAconc / PKNCAdose . 

Implementation Summary:
* Added `pknca_units_table_from_pknca`. Creates a default units table based on a PKNCAconc object (and optionally PKNCAdose as well).

* Introduced helper functions `ensure_column_unit_exists` and `select_minimal_grouping_cols` to support unit column validation and minimal grouping column selection.

* Updated PKNCAdata.default to replace manual unit table construction with the new `pknca_units_table_from_pknca` function.

* Added tests for pknca_units_table_from_pknca to verify its behavior with various scenarios, including:

* Added new imports (dplyr, rlang, tidyr, utils) and exported pknca_units_table_from_pknca to make the new functionality accessible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f37b68cc840`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.