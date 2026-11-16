# Issue

**Title:** Preserve Original Index in NonlinearConstraint Evaluation

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation
This PR only fixes small index handling issue in **```NonlinearConstraint.__call__()```** to preserve the original DataFrame index from input experiments instead of creating a new default integer index.

Currently, when evaluating nonlinear constraints, the implementation returns a **```pd.Series```** with a newly created default index [0, 1, 2, ...], discarding the original index from the input experiments DataFrame. 
**```return pd.Series(    self.expression(**func_input).cpu().numpy())```**

This may cause issues when merging constraint results with other data or tracking which experiments correspond to which constraint values as well as working with non-sequential or custom indices. 

Therefore, it is better to explicitly pass the original index to pd.Series():
**```return pd.Series(    self.expression(**func_input).cpu().numpy(),    index=experiments.index)```**


### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

yes

### Have you updated `CHANGELOG.md`?

yes

## Test Plan

All current unit tests pass with not needed changes. It is simply a logical fix.

Simple verification script outline:

```import pandas as pd
experiments = pd.DataFrame(    
           {'x0': [1, 2, 3], 'x1': [4, 5, 6]},     
           index=[10, 20, 30])
constraint = NonlinearConstraint(...)
result = constraint(experiments)```
#Before: result.index → RangeIndex(start=0, stop=3, step=1) 
#After:  result.index → Int64Index([10, 20, 30])

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55fff4acfeb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.