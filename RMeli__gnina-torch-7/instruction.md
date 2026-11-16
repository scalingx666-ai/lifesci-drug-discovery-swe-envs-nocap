# Issue

**Title:** Use molgrid iteration schemes

## Description

The custom `num_batches` variable was OK for non-balanced, non-stratified sampling but for balanced and stratified sampling `molgrid.IterationScheme` needs to be used in order to define epochs clearly.

* `molgrid.IterationScheme.SmallEpoch`: systems are seen at most once during an epoch
   * For a balanced data set, this means that all examples of the minority class are sampled while examples of the majority class are undersampled
* `molgrid.IterationScheme.LargeEpoch`: systems are seen at least once during an epoch
  * For a balanced data set, this means that all examples of the majority class are sampled while examples of the minority class are oversampled

Here we use the `example_provider` settings in order to define a default `batch_size` and use the underlying iterator with the specified `molgrid.IterationScheme` (which can be user-defined) as a definition of an epoch.

Note: the original implementation uses iterations instead of epochs.

---

Minor changes include:
* `__main__` is now ignored in code coverage; it should only parse arguments and call a function
* `_setup_example_provider_and_grid_maker` is now split into two different functions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4dde7ec60383`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.