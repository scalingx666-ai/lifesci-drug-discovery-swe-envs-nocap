# Issue

**Title:** Match results to a group-stratified units table by value

## Description

When units differ by group (a subject without a dose, or unit columns), the units table keeps group columns as character. `pk.nca()` then stopped with "Can't join `x$subject` with `y$subject` due to incompatible types" for integer, numeric, or Date groups, and silently turned factor groups into character. Repro: integer subject, units given, subject 2 missing from the dose data.

## Fix
`left_join_by_value()` matches the keys as character and keeps the result's own key columns, including the secondary `<group>_ref` columns.

## Tests
The repro, factor preservation, and integer `_ref` matching for `clr.last`.

Stacked on `fix/update-factor-groups`; this PR's diff is only this fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3754aa26c1ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.