# Issue

**Title:** Fix BGF overflow reported by @rphang

## Description

Potential heap-buffer-overflow at bgfformat.cpp:172 CONECT 3 in a 2-atom file previously accepted
Now checks against NumAtoms() since it's unsigned

## Summary by Sourcery

Harden BGF connectivity parsing against out-of-bounds atom indices while retaining valid first-atom bonds.

Bug Fixes:
- Prevent BGF connectivity records from accessing memory outside the atom arrays when indices exceed the molecule size.
- Preserve valid connectivity records for the first atom while rejecting invalid zero or negative indices.

Tests:
- Add fuzz regression coverage for BGF connectivity out-of-bounds input and first-atom connectivity preservation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa562dd8f925`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.