# Issue

**Title:** Document how the concentration counts treat imputed values

## Description

`count_conc_measured` reads as though it counts only measurements, but it counts
by **value**, not by provenance — and neither count knows whether a
concentration was imputed. Found while sweeping parameters against imputation
methods.

| Imputation | `count_conc` | `count_conc_measured` |
|---|---|---|
| none | 6 | 6 |
| `start_conc0` | 7 | 6 — the zero is not above the LOQ |
| `start_predose` | 7 | **7** — a real measurement, moved |
| `start_cmin` | 7 | **7** — fabricated, but above the LOQ |

The `start_cmin` row is the surprising one: a value that was never measured at
that time is counted as measured, because the test is `conc > 0`.

Adds an "Imputed concentrations" section to `pk.calc.count_conc()` documenting
this, notes on `count_conc_measured`'s `@returns` that "measured" means above the
limit of quantification, and says how to count only real samples (calculate the
counts in an interval with no imputation).

A test pins all four cases, so the documented behavior can't drift silently.
No behavior change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58a10b993a17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.