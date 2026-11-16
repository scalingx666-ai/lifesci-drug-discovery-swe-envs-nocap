# Issue

**Title:** Fix pk.nca() error on unsorted concentration-time data

## Description

Group-level concentration data (passed as `conc.group`/`time.group` to
parameters such as `aucint*`) was passed to the calculation routines in
its original row order. Those parameters interpolate/extrapolate over the
full group via `interp.extrap.conc()`, which asserts that time is sorted,
so unsorted input rows caused a "Must be sorted" error.

Fix: sort `data_conc` by time at the top of `pk.nca.intervals()`. The
interval-level data were already sorted per interval, so only the
group-level path was affected.

Adds a regression test (unsorted input matches pre-sorted results across
aucint*, cmax, half.life) and a NEWS.md entry.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58921f3dcc24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.