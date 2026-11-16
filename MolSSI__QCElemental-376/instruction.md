# Issue

**Title:** fix: if verbose, do log info statements

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
there is a small issue in the molecule. a higher verbosity, in general, results in more log messages. however, in the molecule-model, it is implemented the wrong way around. a higher verbosity results in quiet=True, which is not expected.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
fix verbosity of models/molecule.py log messages

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cc11b45b6c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.