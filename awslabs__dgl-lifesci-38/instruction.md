# Issue

**Title:** [Reaction Prediction] Handle Invalid Input Reactions

## Description

As suggested in #18 by @autodataming , we don't want to terminate the prediction process if some reactions cannot be properly handled by the model. With this PR, we perform a first pass to check which reactions can be handled by the model first and record reactions that cannot be handled.

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e834ec6a552a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.