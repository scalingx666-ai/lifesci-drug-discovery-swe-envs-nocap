# Issue

**Title:** Export pknca_difftime_to_unit()

## Description

`pknca_difftime_to_unit()` converts a `difftime` into a number in an analysis time unit; `pk.nca()` uses it for date-time times and `difftime` durations. Packages that derive a duration from date-times (a collection duration, say) need the same conversion and should not reimplement the unit algebra, so it is exported.

- Any `difftime` unit converts exactly, through seconds, to any time unit the units package knows. Hours need no units package; every other unit does.
- It is now strict because it is public. A value that is not a `difftime` stops with `pknca_error_difftime_not_difftime` (a plain number would otherwise be read as seconds). A `unit` that is not a single time-unit string stops with `pknca_error_difftime_unit`, where an unconvertible unit used to give `NA`. The internal callers check the unit first, so `pk.nca()` results are unchanged.
- `pknca_hours_factor()` stays internal; this function covers the conversion.

Tests pin hours, minutes, days, weeks, seconds, date-time differences, `NA`, zero-length input, every error and its class, hours without the units package, and the export. Full suite passes and `R CMD check` is clean apart from the worktree `.git` note.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2542f823134d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.