# Issue

**Title:** add gatv2 model

## Description

*Description of changes:*
- Added GATv2 Layers and GATv2 predictor from DGL, described in [HOW ATTENTIVE ARE GRAPH ATTENTION NETWORKS?](https://arxiv.org/pdf/2105.14491.pdf). Added an implementation test copied from `test_gat`
  - implemented output of attention values for model introspection as used in the paper
  - Not sure if outputting these as a list is the right call, if someone more experienced in pytorch fundamentals/api designs has a suggestion I'm open to it
- fixed an import bug in [test_new_dataset.py](tests/data/test_new_dataset.py) that was preventing pytest discovery when run independent of the `task_unit_test.sh` script

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54649fba5c72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.