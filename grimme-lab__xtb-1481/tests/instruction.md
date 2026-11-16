# Issue

**Title:** Fix free atoms

## Description

This PR adds the functionality to constrain/fix every atom exerpt the ones in the `free` list, which is part of the `$fix` block (the constrain block, respecitvely). This list accepts both atom indicies (also lists) and atom symbols. They can be combined with the other keywords of this input block, howver, the `atoms` and `elements` key "win" over the `free` keyword. This is also coverd in the tests.
This feature might be interesting if e.g. only hydrogens should be optimized.
This feature is also covered in the man page and also a PR for the docs is opened.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `130708f060e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.