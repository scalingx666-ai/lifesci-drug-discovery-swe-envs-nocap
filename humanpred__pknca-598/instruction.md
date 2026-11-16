# Issue

**Title:** docs: regenerate with roxygen2 8.1.0

## Description

Config/roxygen2/version said 8.0.0 while contributors are now running 8.1.0, so every regeneration rewrote NAMESPACE's importFrom directives into 8.1.0's multi-line style and bumped the version field.  That churn appeared in unrelated pull requests and had to be reverted by hand each time; doing it once here stops that.

The change is formatting only.  Parsing both files with parseNamespaceFile() gives identical results: the same 16 imported package/symbol pairs, the same 178 exports, and the same 110 S3 methods.

S3method(AIC,list) is kept.  roxygen2 drops it on every run because R/AIC.list.R is marked @noRd, but removing it would stop AIC() dispatching on lists, which is a behavior change and not part of a formatting commit. It stays hand-maintained.

The dplyr-inherited pages (filter.PKNCAresults.Rd, group_by.PKNCAresults.Rd) are left alone.  Their @inheritParams text comes from the installed dplyr, and dplyr 1.2 wording references when_any() and filter_out() while DESCRIPTION allows dplyr (>= 1.1.0) -- regenerating them here would document functions a supported dplyr does not have and leave a dangling \link.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0533b1cf2a4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.