# Issue

**Title:** Avoid doped checkout failure in macOS CI

## Description

The macOS 14 / Python 3.14 job failed during dependency installation: pip’s VCS install could not switch its doped clone to `develop` because Se example files would be overwritten.

- **CI install:** Clone `develop` directly, then install the checkout:
  ```sh
  git clone --depth 1 --branch develop https://github.com/SMTG-Bham/doped.git "$RUNNER_TEMP/doped"
  pip install --no-deps "$RUNNER_TEMP/doped"
  ```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d715442ab44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.