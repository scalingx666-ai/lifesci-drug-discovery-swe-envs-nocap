# Issue

**Title:** Fix compatibility with pydantic v1.8 / Remove useless connectivity validation

## Description

<!-- Thank you for your contribution! -->

## Description
Removes a useless check of the elements of the connectivity field. This is causing problems due to a breaking change in pydantic 1.8, and is not required anyway due to the values being handled elsewhere.

Previous pydantic behavior for `each_item=True` was to recurse down into nested lists, tuples, etc. The new behavior is to only validate the top level, which for us attempts to compare a `tuple` with an `int`.

But this validator is not required anyway, since now we check with NonNegativeInt and BondOrderFloat.

See https://github.com/samuelcolvin/pydantic/releases/tag/v1.8

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Fix compatibility with pydantic v1.8 w.r.t. connectivity validation

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2582146c6909`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.