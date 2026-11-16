# Issue

**Title:** Add the erint and erlst excretion parameters and fix two CDISC names

## Description

Stacked on #607 — please review and merge that first. Contributes to #157.

## New parameters

The excretion rate over a collection, `conc * volume / duration`, was already
computed inside `pk.calc.ermax()`, `pk.calc.ertmax()`, and `pk.calc.ertlst()`,
but the rate itself was never reported. Both parameters that report it are
standard CDISC terms:

* **`erint`** (`ERINT`, "Excret Rate from T1 to T2") — the amount recovered
  during the interval divided by the interval duration. It uses the interval
  rather than the sum of collection durations, so a gap between collections
  lowers the rate. An interval ending at infinity has no duration to divide by
  and gives `NA` with a reason rather than 0.
* **`erlst`** (`ERLST`, "Last Meas Excretion Rate") — the excretion rate of the
  last collection with a positive rate, ordered by collection midpoint so that
  it is the rate at the time `ertlst` reports. A test pins that pairing.

Both derive `sample_type = "interval"` with no new declaration — `erlst` through
its `volume` formal, `erint` transitively through its `ae` dependency.

## Two corrected CDISC names

Checked against codelist C85839 of the current CDISC SDTM controlled
terminology. Both differed from the standard *and* misstated what the function
returns:

| Parameter | Was | Now (CDISC) |
|---|---|---|
| `ertlst` | Time of Last Excretion Rate | Midpoint of Interval of Last Nonzero ER |
| `volpk` | Volume of PK sample | Sum of Urine Vol |

`pk.calc.ertlst()` computes `time + duration.conc / 2`, so it does return the
collection midpoint, as `ertmax` already said it did.

## Not done here

A wider audit found more CDISC name drift — eight dose-normalized parameters
drop "Norm" (`"AUC All by Dose"` vs `"AUC All Norm by Dose"`), and `mrt.iv.*`
say "Intravasc" where CDISC says "IV Bolus", which is load-bearing since PKNCA
uses those for infusion too. Separate PR.

16 new tests including an end-to-end `pk.nca()` check; full suite passes. The
registry-size gate in `test-001-add.interval.col.R` moves 203 → 205.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `102d57f7e3cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.