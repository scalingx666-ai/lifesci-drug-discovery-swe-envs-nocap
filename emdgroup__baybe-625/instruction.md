# Issue

**Title:** Add Continuous Interpoint Constraints

## Description

This PR adds continuous interpoint constraints.

An interpoint constraint is a constraint that is defined over a whole batch instead of the individual experiments within a batch. The implementation uses the already existing interface from BoTorch for this feautre.
As a consequence, this PR introduces significant changes to the `to_botorch` function of the `ContinuousLinearConstraint` class as this now returns a collection of constraint tuples instead of a single tuple, and thus introduces a breaking change.

Fork docs:
https://avhopp.github.io/baybe_dev/latest/examples/Constraints_Continuous/interpoint.html and https://avhopp.github.io/baybe_dev/latest/userguide/constraints.html#continuous-constraints

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4852652ca0b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.