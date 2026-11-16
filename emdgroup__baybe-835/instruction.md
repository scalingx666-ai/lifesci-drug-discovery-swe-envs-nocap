# Issue

**Title:** Deprecate `SubspaceDiscrete.constraints`

## Description

Finally , enabled by the previous PRs merged to #837.

The `constraints` attribute on `SubspaceDiscrete` conflated two fundamentally different roles:
- *filtering constraints* (applied once during construction to prune the candidate grid) and
- *batch constraints* (applied at recommendation time to enforce structure across the recommended batch)

Storing both under a single field was misleading – filtering constraints are only relevant during construction, and even then only for certain construction routes: when building via `from_dataframe`, the candidate grid is already fully specified by the caller, so filtering constraints were meaningless from the very beginning and had no effect whatsoever. Retaining them on the object after construction served no purpose and gave a false impression that they remained active throughout the object's lifetime. As a further consequence, `from_dataframe` never accepted any constraint objects at all – since filtering constraints are not needed there, and batch constraints were introduced later, users had no way to attach batch constraints when constructing a subspace from a dataframe.

This PR makes the distinction explicit and removes the dead storage:

- **Adds** `SubspaceDiscrete.batch_constraints`: a dedicated field for `DiscreteBatchConstraint` instances that are evaluated during recommendation. `from_dataframe` now accepts a `batch_constraints` argument – fixing the previously missing ability to attach batch constraints when constructing from a dataframe. Filtering constraints passed to `from_product`/`from_simplex` are applied during construction as before and then discarded – there is nothing left for them to do.
- **Deprecates** `SubspaceDiscrete.constraints`: passing it emits a `DeprecationWarning`; any `DiscreteBatchConstraint` instances are automatically migrated to `batch_constraints` to ease the transition.
- **Removes** `is_constrained` properties from `SubspaceDiscrete`, `SubspaceContinuous`, and `SearchSpace`: these were thin Boolean wrappers that obscured which kind of constraint was being checked and, in the discrete case, were backed by the now-meaningless stored filtering constraints.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7a31443d7a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.