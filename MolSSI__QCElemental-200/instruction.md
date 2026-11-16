# Issue

**Title:** Constants: add hbar and fix (?) some units

## Description

<!-- Thank you for your contribution! -->

## Description
This PR adds hbar to constants and fixes some of the units. I don't understand:

1. Were the units "incorrect" intentionally?
2. Why do we have constants separate from the unit registry?
3. Why aren't constants in the unit registry?

## Changelog description
hbar was added to constants. The units of c, kb, h, and dipmom_debye2si were corrected.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bd53fa65b12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.