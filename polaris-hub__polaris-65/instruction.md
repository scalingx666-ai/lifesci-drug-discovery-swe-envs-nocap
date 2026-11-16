# Issue

**Title:** Add additional metadata to the columns, dataset and benchmark

## Description

## Changelogs

**Metadata for benchmarks**
-  
  - Adds the task type (i.e. multi task or single task), computed automatically. 
  - Adds the target type (i.e. regression or classification), can be manually specified, but if not lib tries to infer automatically using [`sklearn`'s `type_of_target()`](https://scikit-learn.org/stable/modules/generated/sklearn.utils.multiclass.type_of_target.html).
  - Adds the train set size, computed automatically. 
  - Adds the test set(s) size(s), computed automatically. 
  - Adds the number of classes for classification tasks, computed automatically. 
  - Adds the number of test sets

**Metadata for datasets**
- 
  - Adds the dtype to the column annotations, computed automatically. 
  - Adds the no. datapoints and no. columns, computed automatically. 
  - Adds a n optional field with a reference to the curation. 

**Misc**
- Add additional syntax to the dataset to make interacting with it easier, similar to `pandas.DataFrame`. E.g. `dataset[row, col]` or `dataset[:, "smiles"]`. 

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee4241872a12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.