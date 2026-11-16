# Issue

**Title:** [Reaction Prediction] Fix for rexgen_direct

## Description

1. Previously we always try loading constructed DGLGraphs in `find_reaction_center_eval.py`. This may not be desired if users have multiple different files for evaluation with a same name. We now change the behavior to constructing DGLGraphs from scratch and users may choose to load existing DGLGraphs if they want.
2. Always pre-process graph edits from scratch.

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e08671d9b8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.