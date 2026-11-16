# Issue

**Title:** Forbid Overlap in Target and Parameter Names

## Description

This PR contains further work to avoid the problem described in the issue. This now works for both stateful and stateless mode. The corresponding validations use the new utility `validate_object_names`

**Notes**:
I've also added the validation to meta-recommenders. This has the consequence that an error will also be thrown if the meta recommender uses a non-predictive recommender which does not use an objective. Overlapping names would not strictly represent a problem for this specific situation, however I would argue this still represents a misconfiguration that should be avoided.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46372e58c18f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.