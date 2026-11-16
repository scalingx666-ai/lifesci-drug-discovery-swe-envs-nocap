# Issue

**Title:** Fold fingerprints to fit into GPU memory, do second-search on full-accuracy on CPU

## Description

This  
This also starts to address #20 - it adds the initial version of fingerprint folding.

@greglandrum - would you mind just looking over the fingerprint folding algorithm?  We added unit tests and think it's matching what RDKit does, but it'd be good to have a quick scan.  We're going to initially do a CPU-only version of folding, but will likely add a GPU version in the future (hence its lack of advanced types).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97319234b19f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.