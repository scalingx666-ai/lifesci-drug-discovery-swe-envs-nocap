# Issue

**Title:** Convert logged dose units to mg in Effect Estimates path

## Description

Effect Estimates passed `DoseEntry.amount` without unit conversion, so `0.08 g` was modeled as `0.08 mg`.
It now converts logged mass units to mg with the same `DoseUnit.convert` call used by tolerance replay, before dividing by the substance reference dose.

| Logged 3-MMC oral dose | Before: EffectEngine tuple `(t, amt)` | After: EffectEngine tuple `(t, amt)` |
| --- | ---: | ---: |
| 80 mg | `(0, 1)` | `(0, 1)` |
| 0.08 g | `(0, 0.001)` | `(0, 1)` |
| 80,000 µg | `(0, 1000)` | `(0, 1)` |

An mL entry has no mass conversion; like tolerance replay, Effect Estimates omits it. No PK, kernel, parameter, or UI behavior was changed.

Verification: iOS build-for-testing passed. Full Swift Testing suite passed with 2,261 tests across 246 suites, including the new unit-equivalence and mL regression test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9dfcd2400f5b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.