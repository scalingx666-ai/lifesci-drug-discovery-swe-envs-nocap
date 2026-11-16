# Issue

**Title:** Models Repr

## Description

This PR attempts to give reasonable string representation for all models and ensure that skip_defaults are called on certain models to prevent the alteration of defaulted fields in downstream Pydantic uses.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `273e5396820f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.