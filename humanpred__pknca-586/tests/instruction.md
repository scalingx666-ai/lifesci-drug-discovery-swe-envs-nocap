# Issue

**Title:** docs: clarify that start_conc0 intentionally forces a zero start concentration

## Description

.

**Behavior change:** `PKNCA_impute_method_start_conc0()` now adds a 0 only when no observation exists at the interval start, matching the skip-if-present semantics of `start_predose`/`start_cmin`. Measured start-time data are no longer silently replaced, and the documented chain `"start_predose,start_conc0"` now genuinely means "predose value if one can be shifted, otherwise zero" instead of collapsing to `"start_conc0"` alone. One existing test pinned the overwrite and was deliberately flipped; roxygen, NEWS (flagged as behavior change), and the v08 vignette passages are updated.

Verification: new tests cover add/skip/chain-with-predose/chain-without-predose (52 pass in the impute file, 568 in adjacent files); the v08 vignette purls clean against the new code.

Note: the PKNCA book documents the old collapse behavior and will need a matching follow-up once this merges.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b337f1ec0e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.