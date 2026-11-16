# Issue

**Title:** Update installation setup to a PEP517 build backend

## Description

<!-- Thank you for your contribution! -->

### Description
<!-- Provide a brief description of the PR's purpose here. -->

Change from the two step build process (meson + setuptools) to a single step build process (meson-python).

### Changelog description
<!-- Provide a brief single sentence for the changelog. -->

- use meson-python as build backend.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `333542176d7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.