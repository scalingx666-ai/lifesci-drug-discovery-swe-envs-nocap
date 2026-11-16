# Issue

**Title:** Restore cached-pattern structure diagram alignment

## Description

`generateAlignedCoordinates(molecule, pattern)` always throws `IllegalArgumentException("No reference provided")` after the reference null check added in 95d90a5802. That overload intentionally delegates with a null reference so the pattern can cache and supply scaffold coordinates, and the three-argument method documents that the reference may be null.

Remove the contradictory reference check, retaining the molecule check and restoring the existing cached alignment path. A regression calls the two-argument overload on ethylbenzene and then benzyl alcohol with the same benzene pattern, checks finite coordinates for every atom, and verifies that the six shared ring atoms keep identical coordinates. The new test fails with the exception before the fix.

Validation: `mvn -o -q -pl tool/sdg -am test` passes: 126 SDG tests and 17,021 tests across the reactor, with zero failures, zero errors and one skipped test. Production and test classes compile with the project's `--release 8` configuration (class version 52).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `178127aa9634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.