# Issue

**Title:** Ability to specify times/durations in config as user-friendly strings

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
For various fields, the config requires you to specify the time something takes in seconds. This is not ideal for long durations (hours to days). This PR adds the ability to specify these in three ways:

* As integer or string seconds (same as before): `90`, `"90"`
* As dhms with a colon separator: `1:04:08:10`  (1 day, 4 hours, 8 minutes, 10 seconds)
* As dhms with a suffix for each part: `1d4h7s` (1 day, 4 hours, 7 seconds)

The conversion code is tolerant of leading zeros and weird quantities (ie, `1d77h99m99s`)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf839b2d3045`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.