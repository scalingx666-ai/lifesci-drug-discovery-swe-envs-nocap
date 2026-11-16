# Issue

**Title:** add equal_phase option to testing

## Description

<!-- Thank you for your contribution! -->

## Description
For when you know expected and computed are only good to a (real) phase but don't want to try/except/else or pre-match the signs. Or for when comparing complex data structure or when only certain leaves are free to negate. This came up for https://github.com/psi4/psi4/blob/master/tests/pytests/test_detci_opdm.py#L47 since `compare_matrices` is `compare_recursive` behind the scenes.

I'd really like a `equal_scaled` option, but that's harder.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc13b57501f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.