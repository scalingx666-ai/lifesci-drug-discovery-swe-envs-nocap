# Issue

**Title:** docs: generate the exclusion rule and imputation method docs from their registrations

## Description

The registration call is now the only place a rule's or method's description is written.  Exclusion rules also register a description of each argument, which pknca_exclude_rules() gives in a new description column of arguments, and imputation methods may register details that follow the description in the documentation.  Each function's roxygen block uses @eval pknca_rd_exclude_rule() or @eval
pknca_rd_impute_method() to write its @describeIn (or @title) and @param tags from the registry, and the pknca_exclude_rules() and pknca_impute_methods() help pages get tables generated the same way.

The argument descriptions are plain text (as the registry shows them), so two option-name fragments join the word list.

Tests: the helpers' output is pinned; every registered rule and method must be documented by an @eval line in its own block (checked from the package source); and one test compares the registry to the installed help (descriptions, argument descriptions, details, and the tables), replacing helper-rd.R and the agreement tests that used it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b460be21479`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.