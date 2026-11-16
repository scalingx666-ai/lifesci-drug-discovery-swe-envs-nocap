# Issue

**Title:** Fix environment variable handling for server & compute config

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Handling of configuring servers and compute managers via environment variables was broken when migrating those to pydantic 2. This implements a more-standard scheme for nesting, letting pydantic largely handle everything

For example, `QCF_DB_DATABASE_NAME` should now be `QCF_DATABASE__DATABASE_NAME` with the two underscores marking the nested model. 

For server config, the function for reading configurations will now test for old environment variables and raise an exception if one is found.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b1b0feadcd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.