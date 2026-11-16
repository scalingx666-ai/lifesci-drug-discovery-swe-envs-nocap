# Issue

**Title:** Minor guidance_update renaming cleanup

## Description

`guidance_update` was renamed to `physical_guidance_update` to disambiguate from other guiding potentials.
A couple of instances of the old name remain in the main branch

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1946267cb38e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.