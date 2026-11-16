# Issue

**Title:** Fix SQLAlchemy 2.1.x compatibility

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Update to SQLAlchemy (2.1 branch) broke some defaults related to unique constraints on generated columns. These are not allowed on virtual columns, which are now implemented in sqlalchemy and made the default. So explicitly mark our generated columns as STORED so that unique constraints work.

Also fixes the URL passed to alembic, resulting in other errors.

Fixes CI errors in PR #1037 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23be93d4f54f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.