# Issue

**Title:** Add allow_zero_in_degree option for gat and gcn models

## Description

This adds the `allow_zero_in_degree` option to be set in the model. This option exists in the base dgl layer objects. This change just adds the option to the GCN and GAT constructors to pass it down to the dgl layer.


By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1e77dbbcdbc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.