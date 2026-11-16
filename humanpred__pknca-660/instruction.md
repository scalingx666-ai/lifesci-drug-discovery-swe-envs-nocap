# Issue

**Title:** Export get_impute_column()

## Description

`get_impute_method()` gives the imputation methods but not where they came from, and for an intervals table with one row a column and a method string give the same length-one value. Packages that report the imputation (nca.reporter's Methods section) need to tell the two apart, so the internal `get_impute_column()` is exported.

- `get_impute_column(intervals, impute)` returns the name of the intervals column the methods are read from: `impute` when it names a column, `"impute"` when `impute` is `NA` and that column exists, and `NULL` when `impute` is a method string or an `NA` with no `"impute"` column.
- It does not read the column, so it does not check that the column is character; `get_impute_method()` does.
- It checks its arguments as `get_impute_method()` did (an atomic scalar `impute`, a data.frame `intervals`), and `get_impute_method()` now relies on it for those checks, so both reject the same inputs.

Tests pin each form, one-row and zero-row tables, the argument errors, the export, and agreement with `get_impute_method()`. Full suite passes and `R CMD check` is clean apart from the worktree `.git` note.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5daa572e230`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.