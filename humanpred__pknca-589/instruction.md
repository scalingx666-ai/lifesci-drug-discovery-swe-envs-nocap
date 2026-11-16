# Issue

**Title:** fix: update.PKNCAresults handles ordered-factor groups and stops warning about unchanged groups

## Description

.

Two fixes: (1) all update-machinery joins now match group keys by value (factor keys coerced to character on join copies only), fixing the vctrs incompatible-ordered-factor error while preserving classes, ordered-ness, and levels in returned data; (2) auto-generated per-group intervals are now filtered to the changed groups like conc and dose already were, so unchanged groups are neither recomputed nor warned about. Plus a guard: an update where no group's data changed returns the existing results with the new data attached (message) instead of erroring on an empty recalculation.

Verification: ordered-factor Theoph update is error-free, warning-free, and `expect_identical` to a full recomputation; unchanged-subject rows byte-identical to originals; character-subject regression guard; the new assertions fail on unfixed main exactly as designed. Full suite: 2,715 pass / 0 fail. The v01 vignette sentence explaining the old warnings is updated (its update example now runs warning-free).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4537f75d644`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.