# Issue

**Title:** Describe the not-calculated abbreviation in the summary caption

## Description

The caption from `summary()` on a `PKNCAresults` object explained every
abbreviation in the table except the one standing in for a value that could not
be calculated, so a reader saw `NC` with nothing saying what it meant.

Each summarized parameter now reports whether it displayed the `not_calculated`
string — as the whole value (`NC`) or as the spread inside the brackets
(`13.5 [NC]`) — and that travels up through the group and object summarizers
alongside the existing `footnote_n`. The caption gains
`<not_calculated>: not calculated` only when some cell actually shows it, so
summaries with nothing not-calculated keep the caption they had. A custom
string is honored: `summary(x, not_calculated = "NoCalc")` yields
`NoCalc: not calculated`.

Also updated the `not_calculated` `@param` text, the sentence in
`vignette("v07-post-processing")` that explained `.` but not `NC`, and
`NEWS.md`. New tests pin both directions, the custom string, and the placement
after the `N`/`n` footnotes; `R CMD check` is clean.



🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5817ec6f88a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.