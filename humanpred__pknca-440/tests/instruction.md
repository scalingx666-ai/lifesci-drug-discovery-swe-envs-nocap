# Issue

**Title:** half.life calculation for intervals involving multiple doses and/or infusions

## Description

Proposal for closing #139 

- Added `time.dose` and `duration.dose` arguments in `pk.calc.half.life` to exclude points from the half-life calculation that occur after last dose end of administration (multi dose and/or infusion). The filtering is only done when the dose arguments are available and not NA.

- Added new details of calculations in `NEWS.md` & `vignette06`

- Added a test to verify that `lambda.z.time.first` correctly shifts based on the `duration.dose` parameter, ensuring the function excludes absorption-phase data points in infusion studies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1457f10b83f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.