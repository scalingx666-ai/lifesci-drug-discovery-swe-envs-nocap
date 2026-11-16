# Issue

**Title:** Psi4 error reporting pre-empted by KeyError

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

Currently, useful error reporting with `psi4` under the `Psi4Harness` can be lost due to a missing `"success"` key on `output_data`. This PR makes attempted access of this key return `False` if not present.

Credit to @dgasmith for pointing this out.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Error messages from `Psi4Harness` no longer swallowed by `KeyError`.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66f10d2f0cdd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.