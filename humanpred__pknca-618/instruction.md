# Issue

**Title:** Add the start_predose_conc0 imputation method

## Description

Contributes to #157 — the imputation half of "make sure that imputation is
covered within the solution".

A new imputation method that uses a predose concentration as the start
concentration when one is available and 0 when it is not:

| Situation | Result |
|---|---|
| Concentration measured at the start time | **kept as-is** |
| Predose sample within `max_shift` | shifted to the start |
| Neither | 0 at the start |

The first row is the point. `start_conc0`'s intent is to force the start
concentration to zero, so after an IV bolus dose it discards a measurement that
*is* the C0 for that dose and forces back-extrapolation instead. The chain
`"start_predose,start_conc0"` cannot express the wanted behavior either, because
`start_conc0` overwrites whatever `start_predose` shifted — `vignette("v08-data-imputation")`
already documented that and told the reader to write their own method for this
case, so it now names this one instead.

## Implementation

It composes the two methods it sits between: `start_predose` first, then
`start_conc0` only if nothing landed at the start time. The tests assert that
equivalence directly rather than comparing against literal data frames — it is
`start_predose` when a predose sample applies and `start_conc0` otherwise. That
is the actual specification, and it will not break when `start_conc0`'s output
shape is tidied (its fallback output currently carries unsorted row names and
varying column order, which this method inherits unchanged).

6 new tests; full suite passes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `506968b592ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.