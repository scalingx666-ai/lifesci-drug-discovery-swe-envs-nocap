# Issue

**Title:** Easily featurize the inputs in the `Subset` class

## Description

## Changelogs

- Adds `featurization_fn` to the `Subset` class and propagates this parameter to the`get_train_test_split()` method.
- Added test cases to ensure the different data formats of the `Subset` class function properly.

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

### Discussion

Throughout user interviews, adding support for easily featurizing the inputs was a common feature request. This PR takes a first step in that direction.

Before:
```python
# Before: Featurization is not part of the Polaris API
train, test = benchmark.get_train_test_split()

# Need to manually featurize the train set
X_train = np.array([dm.to_fp(smi) for smi, y in train])
model.fit(X_train, train.targets) 

# Need to manually repeat the featurization for the test set
X_test = np.array([dm.to_fp(smi) for smi in test])
y_pred = model.predict(X_test)
``` 

After: 
```python

# After: You can now specify a featurization function. 
train, test = benchmark.get_train_test_split(featurization_fn=dm.to_fp)

# No need to manually featurize the train or test inputs
model.fit(train.inputs, train.targets)
y_pred = model.predict(test.inputs)
``` 

#### What about the targets?
There could be benchmarks in which the target would have to be featurized too (e.g. a reaction product). I went down the rabbit hole of also adding a featurization function for the targets. However, this opened up other difficult questions that were difficult to address.

1. `BenchmarkSpecification.evaluate()` does not have a `y_true` parameter to minimize the chance of a user accidentally changing the test labels. However, if we allow a target transformation to be passed to the `get_train_test_split()` method, this means we need to keep track of that function to replicate the correct `y_true` values in `evaluate()`.
2. An additional issue of (1) is that this could lead to ambiguity w.r.t. the test set parameters. What if someone splits a dataset three times with a different target transformation function each time? How would we know which to use once the user calls `evaluate()`? We probably can't, so then it seems important to throw an error if this happens. 
3. People could use also (mis)use this to normalize the output values (e.g. min-max normalization or z-score normalization). Without having an inverse transform, this would lead to a different range for some of the metrics (e.g. MAE, MSE). We could use (something similar to) scikit-learn's scalers (e.g. [here](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html#sklearn.preprocessing.StandardScaler)), but how to differentiate between target featurization (which does not need an inverse) and target normalization (which does need an inverse).

I can see ways around all of the above, but this is out-of-scope for now. We can revisit this once a benchmark actually needs it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08b202d93fbc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.