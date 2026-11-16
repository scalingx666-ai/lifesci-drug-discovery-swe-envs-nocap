# Issue

**Title:** Fix bounded bond ring sizes at even limits

## Description

`Cycles.smallRingSize(bond, max)` can return 0 when `max` is even and the bond's smallest ring has exactly `max` atoms. The search stops after the first atom at the last depth instead of finishing that depth. The Javadoc allows 0 only for acyclic bonds or rings larger than `max`.

At `max = 6` this affects some naphthalene bonds. `StereoElementFactory` uses that limit, so reading a molfile can add an atropisomer to a single bond inside a six-membered ring, for example in rubellin A (COCONUT `CNP0341922.2`).

The test commit fails without the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31b33146b0ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.