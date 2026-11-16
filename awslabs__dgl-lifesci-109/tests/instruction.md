# Issue

**Title:** respect sanitize molecule flag when removing hydrogens

## Description

*Issue #, if available:* None

*Description of changes:*

`Chem.RemoveHs()` has an argument for whether to sanitize molecules, this is `True` by default.
However the user is allowed to specify `Sanitize=False`.
This PR uses the user-specified `sanitize` flag during molecule preprocessing. And passes it to `Chem.RemoveHs`

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

p.s. Nice work guys 👍

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9723c07cb91e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.