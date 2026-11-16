# Issue

**Title:** Estimate the aucint.inf start concentration the same way wherever the interval ends

## Description

With doses at 0 and 12 h and no sample at 12, `aucint.inf.obs` from 12 h extrapolated the start concentration as 0 when the interval ended at or before Tlast, but with the half-life when it ended at Inf, so the 12-24 area did not add up with the area from 12 to Inf. The AUCinf-to-AUClast shortcut for intervals ending before Tlast assumed nothing extrapolated was in the interval, which is false when the start is the trough before the dose that starts the interval.

## Fix
That start is now extrapolated with the half-life in both cases, matching `interp.extrap.conc.dose()` and the existing trough test for the profile before a dose. `PPANMETH` then says "Extrapolation: half-life" and the half-life exclusion applies. An interpolated start still does not use the half-life. Covers `aucint.inf.obs`, `aucint.inf.pred`, and the `aumcint.inf.*` versions.

## Tests
- 12-24 equals `aucint.last` plus half the extrapolated start concentration.
- Additivity: 12-Inf equals 12-20 plus 20-Inf, for `.obs`, `.pred`, and AUMC.
- Method and exclusion attributes; an interpolated start keeps "Extrapolation: none".

Stacked on `fix/ctrough-cstart-interval-start`; this PR's diff is only this fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56517abc3784`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.