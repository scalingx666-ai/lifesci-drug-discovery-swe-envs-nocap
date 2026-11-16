# Issue

**Title:** add handling of CategoricalOutput in aggregrate_by_duplicates

## Description

## Motivation

PR #657 introduces the option to aggregate duplicates in a dataset before doing cross validation, here duplicates are based on input similarity. For this the pre-existing function `domain.aggregate_by_duplicates` is used, but this function was not handling `CategoricalOutput`s and these were dropped from the experiments dataframe. As a result cross validation could throw errors because of missing `CategoricalOutput`s when fitting. This PR addresses this by extending the `domain.aggregate_by_duplicates` to also aggregrate `CategoricalOutput`s, here it was chosen to aggregrate based on majority vote, or randomly when there is a tie. In both cases the user is warned that this is happening, as perhaps the user would not want to aggregrate at all if experiments that are duplicates in the inputs have different CategoricalOutputs.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

### Have you updated `CHANGELOG.md`?

Yes

## Test Plan

Added test case for majority votes with a clear winner.
Added test case for a tie in the majority votes triggering a random pick
Added additional test case for ContiniousInputs with slight variations to test previously untested precision parameter.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c418a5925b66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.