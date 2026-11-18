# Issue

**Title:** Use a resolvable setup-uv release tag

## Description

The Python 3.14 Test Pop job failed before running checks because `astral-sh/setup-uv@v10` could not be resolved.

- **Workflow action refs:** Update the lint and test workflows to use the published `v10.3.3` tag:
  ```yaml
  - uses: astral-sh/setup-uv@v10.3.3
  ```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7020f7c6ef9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.