# Issue

**Title:** Molecule Hash Canary Tests

## Description

<!-- Thank you for your contribution! -->

## Description
Adds all Fractal molecule hash canaries to QCElemental and reverts the order of operations change for hashing molecule in the `from_data` procedure. Hashing molecules is fairly sensitive to the order of operations and this was disrupted slightly when the `from_data` procedure stopped passing the `validate` flag through to the `__init__`. This was primarily done to prevent a duplicate to/from schema, but had the worrying effect that the geometry was not correctly rounded. A new flag has been introduced to fix this particular issue.

## Changelog description
Fixes a Molecule hashing issue due to order of operations changes in `Molecule.from_data`.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd1eeeffd865`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.