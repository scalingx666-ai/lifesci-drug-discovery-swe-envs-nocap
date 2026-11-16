# Issue

**Title:** Add explicit Sphinx configuration path to .readthedocs.yaml

## Description

ReadTheDocs deprecated automatic detection of Sphinx configuration files. This commit adds an explicit sphinx.configuration: docs/conf.py entry to .readthedocs.yaml to ensure compatibility with their policy change (effective Jan 20, 2025).

Reference: https://blog.readthedocs.com/posts/2024-06-17-deprecate-implicit-config/

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6180f9c3d785`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.