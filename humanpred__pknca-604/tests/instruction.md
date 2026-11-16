# Issue

**Title:** Error when a volume-dependent parameter is requested without a volume

## Description

Requesting `ae` (or anything downstream of it, such as `clr.last` and `fe`) without giving `volume` to `PKNCAconc()` reported the parameter as not calculated instead of saying that the input was never supplied.

`PKNCAconc()` always creates a volume column and fills it with NA when none was given, so absence is detected by value.  A volume missing for only some measurements is left to the existing per-interval missing-data exclusions.

Which parameters need a volume is derived from the dependency walk added for issue 538 rather than listed by hand, so `set_requires_dose()` becomes `set_requires_inputs()` and caches a fourth `requires_volume` flag from the same walk.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b934cf9da2fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.