# Issue

**Title:** fix: fail loud on non-logical half-life point columns and annotate unreportable half-life

## Description

.

(1) Non-logical `exclude_half.life`/`include_half.life` columns (e.g. `"yes"`, which silently excluded nothing) now error with an informative message at both `PKNCAconc()` construction and again at `pk.nca()` time (catching post-construction mutation). (2) When no λz window survives the selection gate — including the case where a well-fitting λz ≤ 0 window anchors the adjusted-R² tolerance — the NA half-life now carries an exclusion reason via the standard `attr(result, "exclude")` mechanism, in both the log-linear and Tobit branches. Normal fits, the too-few-points path, and manual selection are unaffected.

Verification: full suite 2,717 pass / 0 fail (the 2 warnings are pre-existing on baseline); new tests pin the exact error messages, the new exclusion reasons (direct call and through `pk.nca()`), and clean exclude columns for healthy fits.

Note: a typo'd column *name* passed to these arguments still silently creates an all-NA "not in use" column — a separate silent path possibly worth its own issue.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad5e9f253b01`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.