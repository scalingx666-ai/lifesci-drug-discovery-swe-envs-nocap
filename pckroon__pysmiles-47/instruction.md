# Issue

**Title:** Hypothesis overhaul

## Description

This PR completely overhauls the hypothesis tests to make it generate only chemically valid molecules. Note that chemically valid is a bit of a stretch, since `c1cc-2ccc12` is considered valid.
This makes the hypothesis tests *much* faster.

It uncovered some issues with the aromaticity code involving 0-order bonds and `*`-atoms. `mark_aromatic_edges` was *way* to aggressive in setting aromatic bond orders; it now only affects bonds that are in a cycle of aromatic atoms.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c43ff4455a69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.