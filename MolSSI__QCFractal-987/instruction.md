# Issue

**Title:** Remove using BaseModel.Config as base class for pydantic model Config

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

In a few places we derived the pydantic model's Config class from BaseModel.Config. This was causing sphinx build issues, but also doesn't seem to be appropriate (based on the examples in the pydantic documentation). So the inheritance of that base class has been removed.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `006e07634fcf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.