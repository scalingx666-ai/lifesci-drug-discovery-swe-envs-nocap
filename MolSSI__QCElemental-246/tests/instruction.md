# Issue

**Title:** Replaces deprecated numpy dtypes

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Replaces deprecated data types np.float/np.int/np.bool with native float/int/bool.
See [Notes](https://numpy.org/devdocs/release/1.20.0-notes.html) in v1.20.0 on Deprecations.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34c259f0c759`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.