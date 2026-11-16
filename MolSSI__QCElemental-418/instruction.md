# Issue

**Title:** Fix units registry for pint 0.26.2 CODATA unit braces

## Description

pint 0.26.2 raises on unknown operators instead of ignoring them, so the LaTeX-style exponents in CODATA unit strings (e.g., "J^{-2}") broke build_units_registry and thus test collection. Convert braces to parentheses before defining the atomic units. Tested with pint 0.24.4, 0.25.3, and 0.26.2.

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `bash scripts/format.sh` in the base folder or use pre-commit. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca4939ab6a09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.