# Issue

**Title:** fix: warn instead of erroring on over-length parameter descriptions

## Description

The 40-character limit on `desc` in add.interval.col() was enforced with a checkmate assertion, so a description one character too long aborted the call. Because packages register their parameters at load time, that turned a formatting concern into an install-blocking error downstream.

A revdep check found aNCA cannot be installed against the development version at all: its "The sum of urine volumes for the interval" description is 41 characters, and the failure happens during lazy loading, before anything in aNCA can run. The GitHub version carries two further descriptions of 88 and 96 characters.

Keep the SDTM guidance and report it as a warning naming the parameter, its length, and the offending text, while still registering the description. Packages that supply a longer one keep working and can shorten it before an SDTM submission. Invalid `desc` values (NA, empty, length other than one) still error as before.

Reword the existing NEWS entry rather than adding a new one, since the limit has not appeared in a release.

Tests: 4054 passing, 0 failures.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b36799fd633`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.