# Issue

**Title:** Aggregate duplicates before cross validation

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

The Feature Request has been specified and discussed in #657 

Currently cross validation is applied on all experiments passed to the cross_validate method, if there are duplicates in the dataset, data leakage can lead to positively distorted model metrics. 

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

### Have you updated `CHANGELOG.md`?

Yes

## Test Plan

### Added a test case `test_model_cross_validate_aggregate` to verify if samples are correctly aggregated:

The input contains 5 samples with two duplicated inputs.
```python
   experiments = pd.DataFrame({
        "x_1": [1.0, 1.0, 2.0, 2.0, 3.0],
        "x_2": [1.0, 1.0, 2.0, 2.0, 3.0],
        "y": [1.0, 2.0, 3.0, 4.0, 5.0],
    })
```

This test verifies if the number of samples becomes 3 after aggregation. And also tested compatibility to see if number of samples is 5 when `aggregate` is set to `False`.

### Modified a test case `test_model_cross_validate_groupfold` to add validation of aggregate is correctly switched off when group fold is supplied:

```python
    # Test if aggregate fallback to False when group split is supplied
    with pytest.warns(
        UserWarning,
        match="Aggregation is not compatible with group split, fallback to no aggregation.",
    ):
        train_cv, test_cv, hook_results = model.cross_validate(
            experiments,
            folds=4,
            aggregate=True,
            random_state=random_state,
            group_split_column="group",
        )
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4c932011777`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.