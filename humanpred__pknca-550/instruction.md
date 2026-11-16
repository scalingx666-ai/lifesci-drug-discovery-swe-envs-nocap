# Issue

**Title:** Clarify sparse grouping in the sparse NCA vignette

## Description

## Summary

Addresses [discussion #530](https://github.com/humanpred/pknca/discussions/530), where a user asked how sparse sampling groups samples when the concentration formula has several grouping variables — e.g. `conc~time | matrix + drug + usubjid / analyte`. The vignette didn't explain the behavior, leaving it unclear whether samples are combined by `usubjid`, by a single grouping variable, or by the full combination.

The answer (and the actual behavior in the code) is that sparse parameters pool **all subjects that share the same concentration grouping variables with the subject column removed** — so the example above pools by `matrix + drug + analyte`.

## Changes

- **`vignettes/v04-sparse.Rmd`** — New section "How Subjects Are Grouped for Sparse Calculations" that:
  - explains sparse parameters are computed from the *pooled* samples of every subject in a group (vs. per-subject for dense PK);
  - states the rule: groups are the `PKNCAconc()` formula's grouping variables with the subject column removed;
  - walks through the exact multi-variable example from the discussion, showing `usubjid` is the subject and pooling is therefore by `matrix + drug + analyte` together — not by `usubjid` separately, and not by any single variable alone;
  - notes that all subjects in a group must share the same dosing, or PKNCA errors.
- **`NEWS.md`** — Entry under `## Improvements` referencing #530.

## Verification

- Claims checked against the grouping code: `setdiff(group_cols_selected, subject)` in `R/prepare_data.R`, subject default in `R/class-PKNCAconc.R`, and the shared-dosing check in `R/prepare_data.R`.
- `spelling::spell_check_files()` on the vignette: no errors.
- Vignette renders to HTML cleanly.

Docs-only change; no code or tests affected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70930eba83e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.