# Issue

**Title:** add support for custom formulas with  categoricals and discrete

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

Using a custom formula with categoricals, as in
```
    # Create a domain with categorical, continuous, and discrete variables
    inputs = Inputs(
        features=[
            CategoricalInput(
                key="color",
                categories=["red", "blue", "green"],
            ),
            CategoricalInput(
                key="material",
                categories=["plastic", "metal"],
            ),
            ContinuousInput(
                key="temperature",
                bounds=(20.0, 100.0),
            ),
            DiscreteInput(
                key="pressure",
                values=[1.0, 2.0, 3.0, 5.0, 10.0],
            ),
        ]
    )

    domain = Domain(
        inputs=inputs,
        outputs=[ContinuousOutput(key="y")],
    )

    # Define a custom formula with interactions among categorical variables
    custom_formula = "color + material + temperature + pressure + color:material"

    # Create DoE strategy with the custom formula
    data_model = data_models.DoEStrategy(
        domain=domain,
        criterion=DOptimalityCriterion(formula=custom_formula),
        verbose=True,
        scip_params={"parallel/maxnthreads": 1},
    )
    strategy = DoEStrategy(data_model=data_model)

    # Get required number of experiments
    n_exp = strategy.get_required_number_of_experiments()
```
creates an error 
```
Exception has occurred: FactorEvaluationError       (note: full exception trace is shown but execution is paused at: <module>)
Unable to evaluate factor `material`. [NameError: `material` is not present in the dataset or evaluation context.]
NameError: `material` is not present in the dataset or evaluation context.
```
### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

yes

## Test Plan

Test that the code above runs and individual tests to check that custom formulas are modified to contain the expected categorical values as variables (one-hot encoded)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58a017523ecb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.