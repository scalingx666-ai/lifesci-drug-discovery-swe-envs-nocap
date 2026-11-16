# Issue

**Title:** Refactor/Chore: Remove access parameters in client

## Description

This PR removes the `AccessType` type, simplifying the API by eliminating the `access` parameter, which was previously used to specify public or private access when uploading artifacts to the Polaris Hub.

### Removal of `AccessType` and `access` parameter:

* **Type and Imports Cleanup**:
  - Removed `AccessType` from imports in multiple files, including `polaris/benchmark/_base.py`, `polaris/dataset/_base.py`, `polaris/dataset/_dataset.py`, `polaris/dataset/_dataset_v2.py`, `polaris/evaluate/_results.py`, `polaris/hub/client.py`, and `polaris/model/__init__.py`.

* **Parameter Removal in Method Definitions**:
  - Removed the `access` parameter from method signatures such as `upload_to_hub` in various modules (`polaris/benchmark/_base.py`, `polaris/dataset/_base.py`, `polaris/dataset/_dataset.py`, `polaris/dataset/_dataset_v2.py`, `polaris/evaluate/_results.py`, `polaris/hub/client.py`, and `polaris/model/__init__.py`). 

* **Documentation Updates**:
  - Adjusted method docstrings to remove mentions of the `access` parameter, ensuring the documentation aligns with the updated API.
  
  Notion Package: https://www.notion.so/Private-Artifact-Removal-1ec0c0d8de7080cf9b6fdde6b7fc0dd8

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d5af2c24444`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.