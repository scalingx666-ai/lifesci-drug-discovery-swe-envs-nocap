# Issue

**Title:** update after pint v0.20 rearrangement

## Description

<!-- Thank you for your contribution! -->

## Description
The pint v0.20 release rearranged its internals such that qcel was throwing ` cannot import name 'quantity' from 'pint' `. This  rearranges our imports such that pre- and post-0.20 pint work.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `295642189fe3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.