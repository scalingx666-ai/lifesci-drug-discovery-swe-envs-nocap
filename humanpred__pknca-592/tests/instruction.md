# Issue

**Title:** docs: metadata and dead-code cleanups (normalize_by_col title, NEWS, duplicate registrations, setRoute)

## Description

.

Applies the grab-bag: `normalize_by_col()` retitled as user-facing; the NEWS sparse bullet corrected to the actual five sparse-derived parameters (`mrt.sparse.last`, not `mrt.ivint.last`) and reworded from "sparse AUC parameters"; a NEWS entry added for `PKNCA_impute_method_end_conc_drop`; the stale source comment now points at `vignettes/v80-writing-parameter-functions.Rmd`; the duplicated `add.interval.col()` registrations for the five sparse-derived parameters removed (registry proven `identical()` before/after, and a new test pins single registration plus total registry size); the unreachable `message_if_default` wiring removed from `setRoute` with a comment that the route defaults silently by design.

Verification: 345 tests pass across the touched areas.

Note: `setDuration` has the same dead `message_if_default` pattern — left out of scope here.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee7eec74de5f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.