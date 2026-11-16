# Issue

**Title:** github: add package source dir to coverage

## Description

- Add package source directory to the coverage call.
      Otherwise completely untested files not called in
      the unittests would slip through CI/CD pipeline.
    - Now completely untested files will be in the
      coverage report with 0% coverage.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `634ecc453cda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.