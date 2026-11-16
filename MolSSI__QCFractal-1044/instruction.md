# Issue

**Title:** Internal job improvements (and manager test fixes)

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Improves internal jobs (and some manager test)

Some locking issues and inconsistent behavior was discovered during investigating flaky tests. Turns out those test were indeed failing due to some bugs related to timing-sensitive multi-thread behavior in the internal jobs.

This also fixes some flaky manager tests.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `318acab087cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.