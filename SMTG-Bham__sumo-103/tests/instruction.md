# Issue

**Title:** BUGFIX: Write primitive cell from kgen when using CASTEP

## Description

Bug reported in 

The Castep implementation overlooked a block in kgen which writes a
primitive cell file when non-primitive input was provided. This should
be harder to overlook; consider implementing a more consistent
interface for additional codes?

Anyway, this PR adds a Structure importer to the CastepCell class in order to complete the required functionality. It's a bit inelegant.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f07da8f532e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.