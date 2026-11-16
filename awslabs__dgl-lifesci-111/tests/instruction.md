# Issue

**Title:** Update import from dgl to dgl.data.utils

## Description

*Description of changes:*
Updated an outdated import from dgl to point to dgl.data.utils where the save_graphs and load_graphs packages now live according to https://docs.dgl.ai/en/0.4.x/api/python/data.html#utils

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `112ecb13b9f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.