# Issue

**Title:** feat(cdisc): give every PP row its SDTMIG time point reference

## Description

`as.data.frame(out_format = "cdisc")` now describes each row against one time point reference, as SDTMIG 3.4 defines it. PPSTINT and PPENINT are relative to the reference named in the new PPTPTREF column, and PPRFTDTC is that reference's date-time.

Before, PPSTINT and PPENINT were filled only for "INT" parameters and measured from the last dose. PPRFTDTC was the subject's first dose, and nothing set PPTPTREF, so the columns of one row could describe different references.

The convention:
- The reference is the dose that starts the interval: the last included dose at or before the interval start for that subject and group (PPTPTREF "LAST DOSE PRIOR TO INTERVAL"). A steady-state interval reads PT0H to PT24H.
- A subject without an included dose uses its first concentration (PPTPTREF "FIRST OBSERVATION"), the same fallback as the date-time references, so it agrees with `time_reference_type`.
- PPSTINT and PPENINT are given for every parameter, in `timeu_pref`. PPENINT is NA for an interval to infinity.
- With date-time input, PPRFTDTC is the date-time of each row's reference, so it can differ between intervals of one subject. Numeric input still has no PPRFTDTC.
- Negative durations are written "-PT0.5H", and durations are never in scientific notation.

PKNCA is now the source of truth for these columns, so nca.reporter can stop recomputing them.

Tests cover a single dose, a steady-state interval, an interval starting between doses, excluded doses, an interval before the first dose, a subject without doses, a dose formula without the subject, minutes-to-hours conversion, sparse data, per-row PPRFTDTC, and column order.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `250ac78dbddb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.