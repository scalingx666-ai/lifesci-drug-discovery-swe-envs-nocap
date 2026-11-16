# Issue

**Title:** undo overzealous autodocs removal

## Description

<!-- Thank you for your contribution! -->

## Description
Removal of home-grown autodoc in #289, while good, threatened to break `qcportal`/`qcfractal` import. Presence restored, though not functionality (which interfered with autodoc-pydantic).

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3766e37f0e2a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.