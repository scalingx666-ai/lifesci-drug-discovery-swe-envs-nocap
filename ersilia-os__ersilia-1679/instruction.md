# Issue

**Title:** add exception for contributor, it can be none

## Description

This pull request introduces a change in the `contributor` setter method in the `ersilia/hub/content/base_information.py` file to handle cases where the input is `None`, `"none"`, or `"null"` more gracefully.

### Key change:

* [`ersilia/hub/content/base_information.py`](diffhunk://#diff-00769b60d1f1618f896dfd817e6cbe242c2ee57685c72053b4751b15371cdae1R1674-R1678): Updated the `contributor` setter method to set `_contributor` to `None` if the input is `None`, `"none"`, or `"null"`, improving robustness in handling these special cases.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3df7cadf6ddb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.