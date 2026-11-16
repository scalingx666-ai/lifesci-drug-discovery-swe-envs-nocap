# Issue

**Title:** Choose automatic intervals by regimen segment after a change of regimen

## Description

## Summary
- When `find.dose.regimen()` finds more than one segment in a group's dose times and the design is dense, `choose.auc.intervals()`, and so `PKNCAdata()`, choose the intervals by segment:
  - one steady-state interval for each segment, its last complete cycle at its own period, ending at the recorded dose that starts the next cycle;
  - the interval after the first dose;
  - the interval after any other dose only when it is sampled densely.
- Sampled densely means at least `dense.samples` samples, 3 by default, within one period after the dose. Each sample with a concentration counts once: by its nominal time when it has one, otherwise by its actual time.
- The last dose uses the last segment's period, even when an earlier segment has more doses.
- A new `pknca_warning_intervals_by_segment` warning, also a `pknca_warning_tau_regimen_change` warning, names the segments and the intervals chosen.
- Nominal times must share the actual times' origin. Nominal times that restart at each dose fall back to actual times with `pknca_warning_intervals_nominal_restart`. The nominal times and `conc` are checked, with classed errors, only when they are used.
- `choose.auc.intervals()` gains `time.conc.nominal`, `time.dosing.nominal`, `dense.samples` and `conc`. `PKNCAdata()` passes the `time.nominal` columns and the concentrations.
- Each dose is matched to its place in the regimen. A dose recorded a little early stays in its own cycle, and two doses less than a period apart at the same place are not one cycle. So no steady-state or last-dose interval contains a later recorded dose.

## Behaviour changes
- Dense data with a regimen change used to get an interval for every sampled dosing interval, plus a last-dose interval at the period of the segment with the most doses. They now get the per-segment intervals above.
- Sparse data and single regimens keep their intervals, except where the interval for the last dose used to contain a later recorded dose. Once-daily doses at 0, 24.3 and 47.8 h used to give 24.3-48.3, and now give the last cycle from 47.8. When the last two doses are less than a period apart at the same place, the interval now starts at the last dose.

## Tests
- New tests in test-choose-intervals.R cover:
  - per-segment intervals in both directions, and three segments;
  - the last segment's period;
  - recorded-dose ends with jitter and with a missed dose;
  - collapsed last cycles;
  - the density threshold and per-sample counting rules;
  - nominal restarts and input checks;
  - sparse data;
  - the `PKNCAdata()` path.
- test-pk.calc.all.R checks `pk.nca()`'s `aucint.last` against a hand trapezoid.
- The full suite passes, and R CMD check gives 0 errors and 0 warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77589af0ef16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.