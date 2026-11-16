# Issue

**Title:** docs: clarify three-state include/exclude_half.life semantics

## Description

## Summary
The `TRUE`/`FALSE`/`NA` semantics of `include_half.life` / `exclude_half.life`, and
the rule that only one may be in use per interval, were not in the argument
reference. This made it non-obvious that initializing a column to all-`FALSE`
(instead of `NA`) *engages* that mechanism, which can trigger "Cannot both include
and exclude half-life points for the same interval" when inclusions are also set.
(Surfaced by an aNCA revdep check against dev PKNCA.)

## Changes
- Roxygen / man pages (`PKNCAconc()`, `pk.nca.interval()`): document the three
  per-point states (`TRUE` acts, `FALSE` does not, `NA` undefined), the activation
  rule (a column is "in use" unless entirely `NA`, so an all-`FALSE` column still
  counts), and the mutual-exclusivity rule.
- Half-life vignette (`v06`): add the same note; fix a mislabeled `include_half.life`
  example (intro text said "exclude"; chunk comments were copied from the exclude case).
- NEWS entry under Improvements.

Documentation only — no behavior change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6be00f7b1920`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.