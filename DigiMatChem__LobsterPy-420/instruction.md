# Issue

**Title:** Update featurizer

## Description

# Changes

- Include charge statistics (min, mean, max, std) in DataFrame returned by `ChargeFeaturier`
- Adapt and update tests to reflect the changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2fc69ff7e45`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.