# Issue

**Title:** Refactor Catalog command

## Description

This PR introduces more changes to make the catalog command simpler:

- [x] Catalog command should show a table by default. Consolidate --as-table / --as-json option.
- [x] Catalog command should show the identifier and slug by default when the --more option is not used
- [x] Catalog --browser eliminate and consolidate --local/--hub
- [x] Harmonize the --more flag: Identifier, Slug, Title, Task, Input shape, Output, Output shape, Model source (if local)
- [x] Sort models by ID
- [x] Index in the table to know how many models are there

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82e820023d37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.