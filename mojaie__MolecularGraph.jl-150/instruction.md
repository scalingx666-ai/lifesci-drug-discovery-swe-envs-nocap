# Issue

**Title:** Respect NumHydrogens in cdxml format

## Description

Currently the 'NumHydrogen' parameter is being ignored in CDXML files.

This PR adds a field num_hs to CDXMLAtom in order to make the atom aware of the setting.

In order to correctly print the molecule, `printv2mol()` had to be modified by an optional array of implicit hydrogens and a respectively formatted atom line.

There's no regression in performance and all tests pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ee6cbe15b37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.