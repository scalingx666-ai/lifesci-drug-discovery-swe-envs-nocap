# Issue

**Title:** adapt for numpy v2

## Description

<!-- Thank you for your contribution! -->

- [x] Ok, this fixes up qcel for numpy v2. But poetry won't actually let me specify the loosest constraints (use pint v0.24 if numpy v2), so pyproject.toml a little more restrictive than reality.
- [x] ~also adds chg/mult to Molecule repr -- that's for eyes so should be harmless.~ moved to #340

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e5a8cff52a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.