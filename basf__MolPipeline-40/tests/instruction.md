# Issue

**Title:** .github: add test coverage with threshold

## Description

- Execute the unittests with the coverage module instead
      of using the unittests module directly.
    - Introduce a threshold for code coverage. If the coverage
      will shrink below the threshold the CI/CD pipeline will
      fail.
    - Collect coverage separately for the core test suite and
      extra packages like chemprop.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01d83008c56d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.