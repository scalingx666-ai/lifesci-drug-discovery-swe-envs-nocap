# Issue

**Title:** Removed XGBoost and removed scikit-learn version constraint.

## Description

Removed scikit-learn package version upper bound. (experimental-design/bofire#651)

Co-authored by:
@phibuc
@kobald_boehcp

## Motivation

The scikit-learn package version was restrained by XGBoost.
As discussed during the hackathon XGBoost was removed and the scikit-learn package version constraint has been removed.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan

I ran pytest -v.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72b1565c665a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.