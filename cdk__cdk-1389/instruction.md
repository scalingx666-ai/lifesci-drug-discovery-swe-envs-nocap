# Issue

**Title:** If we provide a builder to the SmartsPattern we should create a non-q…

## Description

…uery AtomContainer. This means the atoms/bonds know about their indices in that query container.

Longer term I think we can probably do away with the QueryAtomContainer completely and just have AtomContainer's with query features. The only tricky one is pharmacophore.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6341aa6324a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.