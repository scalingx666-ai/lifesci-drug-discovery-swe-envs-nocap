# Issue

**Title:** fix(ci): use pdm in publish workflow

## Description

## Summary
- publish workflow was failing because \`pip install .[dev]\` doesn't pick up PEP 735 dependency-groups
- aligned it with the CI workflow's pdm-based setup
- needed before the next release (v3.5.1 release got a GH tag but never made it to PyPI)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5b69aba3121`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.