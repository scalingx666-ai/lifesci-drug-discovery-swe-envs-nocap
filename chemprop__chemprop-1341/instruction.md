# Issue

**Title:** fix type of `_T_default_criterion` and `_T_default_metric` in `_FFNPredictorBase`

## Description

## Description
`_T_default_criterion` and `_T_default_metric` are references to the class, not to an initialized object from the class. Hence, the correct type would be `type[ChempropMetric]`, rather than `ChempropMetric`

## Example / Current workflow
-

## Bugfix / Desired workflow
-

## Questions
If there are open questions about implementation strategy or scope of the PR, include them here

## Relevant issues
If appropriate, please tag them here and include a quick summary

## Checklist
- [x] linted with flake8?
- [x] (if appropriate) unit tests added? -> I will not add a linter for type checks :D

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bcab5b3f2ead`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.