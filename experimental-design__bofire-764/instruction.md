# Issue

**Title:** Added a new function for validating strictly increasing objective bounds instead of monotone increasting

## Description

## Motivation
This PR tightens objective bounds validation and aligns tests with the intended behavior.

Previously, objective bounds accepted non-strict bounds. For IdentityObjective-based objectives, that can create degenerate normalization ranges and lead to unstable behavior. This change enforces strict bounds for objectives so lower must be strictly less than upper.

To avoid unintended side effects, monotonic validation in shared type utilities remains available for other non-objective uses.

While running the related tests, I also found a deprecation warning for FactorialStrategy during serialization specs and updated the serialization test to explicitly expect that warning.

## Have you read the Contributing Guidelines on pull requests?
Yes.

## Have you updated CHANGELOG.md?
Yes. Added entries for:

- strict objective bounds validation behavior
- serialization test handling for FactorialStrategy deprecation warning
- testing that domains reject bad objectives

### Test Plan
Added strict validator test coverage in test_types.py:

rejects decreasing
rejects equal adjacent values
accepts strictly increasing sequences

Updated objective invalid specs in objectives.py:

MaximizeObjective with equal bounds is invalid
MinimizeObjective with equal bounds is invalid

expected error matching aligned with [identity.py] validator
Updated serialization test in test_serialization.py:

explicitly expects DeprecationWarning for FactorialStrategy

Added regression coverage for Domain.model_validate_json(...) with [bad_objective_bounds.json]

#### Ran:

[test_types.py]
objective-invalid slice in [test_invalid.py]
strategy serialization path in [test_serialization.py]
full data-model suite under data_models

Outcome:

strict objective bounds behavior validated
non-objective monotone behavior preserved
full data-model suite passed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f563e5343eb2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.