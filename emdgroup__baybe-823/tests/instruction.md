# Issue

**Title:** Add GaussianProcessSurrogate.posterior_mean_function

## Description

Adds a posterior_mean_function method to GaussianProcessSurrogate. It lets you use a trained GP's posterior mean as the prior mean of a new GP:

    pretrained_gp = GaussianProcessSurrogate()
    pretrained_gp.fit(searchspace, objective, measurements)

    new_gp = GaussianProcessSurrogate(mean_or_factory=pretrained_gp.posterior_mean_function)
    new_gp.fit(new_searchspace, objective, new_measurements)

## Why the normalization handling is needed

Every GP in BayBE normalizes its inputs based on the bounds of the search space it was trained on. So when we reuse a pretrained GP's mean inside a new GP, we have to be careful: the new GP normalizes inputs with its own bounds before handing them to the mean.

For example, say the pretrained GP was trained on x in [0, 5] and the new one on x in [0, 10]. The point x = 2.5 becomes 0.5 for the old GP but 0.25 for the new one. If we passed that 0.25 straight through, the pretrained GP would read it as 1.25, which is the wrong point.

To avoid this, the mean module undoes the new GP's normalization before querying the pretrained GP, and re-standardizes the output back into the new GP's y-space. These transforms are built at fit time, once the new search space is known.

## How it works

- posterior_mean_function can be passed straight to a new surrogate as mean_or_factory. At fit time it wraps a frozen copy of the pretrained GP in a GPyTorch mean module.
- The pretrained GP is frozen and in eval mode, so it only contributes its posterior mean and is not retrained.
- Since it wraps a live BoTorch model, a surrogate using this mean cannot be serialized.
- Calling it on an unfitted surrogate raises ModelNotTrainedError.

## Tests

Added in test_gp.py:

- A new GP trained on data lying on the pretrained mean reproduces the pretrained GP prediction, including across different search space bounds.
- Fitting the new GP leaves the pretrained GP hyperparameters untouched.
- The mean works both as a reusable pre-built module and as a factory.
- Calling it before fitting raises ModelNotTrainedError.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9b0e2230f24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.