# Issue

**Title:** bugfix: NoneType not iterable when inference_pocket_constraints is None

## Description

`Featurizerv2.process_contact_feature_constraints` raises:<br>`TypeError: 'NoneType' object is not iterable` <br>when either `inference_pocket_constraints=None` or `inference_contact_constraints=None` and `compute_constraint_features=True`.

Proposed solution is the minimal diff (also added explicit typing to the function to show that the constraint arguments are not `Optional` in this function (unlike above in the file))

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f868e6403dea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.