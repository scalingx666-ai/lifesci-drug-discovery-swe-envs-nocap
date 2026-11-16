# Issue

**Title:** [Model] Set Bias to be True by default for GAT and GATPredictor

## Description

There's a bug in `GATConv` as of DGL 0.6.1 that the module tries to reset bias even when `bias=False`. While this has been fixed in the master branch of DGL, users can easily encounter the issue with DGL 0.6.1.

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c48700ddfaf4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.