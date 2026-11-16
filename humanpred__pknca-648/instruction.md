# Issue

**Title:** Add pknca_impute_methods(), a registry of imputation methods

## Description

Adds pknca_impute_methods(), which lists PKNCA's imputation methods with the names imputation strings use, the function names, one-line descriptions and the arguments with their defaults. It is built like pknca_exclude_rules(): each method is registered with its description beside its definition, with no documentation parsing at run time. Tests require every exported PKNCA_impute_method_* function to be registered and resolvable through PKNCA_impute_fun_list(), and, against the installed help, each method's documentation to begin with its registered description. The Rd test helpers move to tests/testthat/helper-rd.R and the argument helper is shared with the exclusion registry. pknca.ai's catalog_impute() will wrap this.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d9c0e5bd884`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.