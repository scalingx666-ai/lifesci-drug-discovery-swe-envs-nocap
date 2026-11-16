# Issue

**Title:** docs: document filter_interval's actual start-time-only selection

## Description

.

The incorrect "beginning and ending" sentence existed only in the v03 vignette (already corrected in #576), and no R documentation described interval data selection at all — so this documents the actual rule everywhere it belongs: new roxygen for the internal `filter_interval()`, a details paragraph in `pk.nca()` (including that a dose exactly at `end` is excluded), the same paragraph in `check.interval.specification()`, and an expanded `duration` argument doc in `PKNCAconc()`. No behavior change. If implementing the duration-aware rule is preferred instead, that supersedes this — see the issue discussion.

Verification: 653 existing tests across the four touched areas pass; only the four intended man/ files regenerated.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3eb5d4a8e3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.