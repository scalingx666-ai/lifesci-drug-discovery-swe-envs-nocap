# Issue

**Title:** Exclude test assets from GitHub Pages artifact to unblock deploy job

## Description

The `pages build and deployment` workflow’s `deploy` job failed after artifact upload, despite a successful build. The published Pages artifact was including repository test content that is irrelevant to the site output.

- **Change**
  - Added a root Jekyll config to exclude `tests/` from GitHub Pages packaging.
  - This narrows the Pages artifact to site content only and avoids deploying non-site files.

- **Files**
  - `/_config.yml` (new)

- **Config snippet**
  ```yml
  exclude:
    - tests/
  ```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb8f35960c90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.