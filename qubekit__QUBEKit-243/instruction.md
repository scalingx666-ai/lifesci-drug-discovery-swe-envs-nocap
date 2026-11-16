# Issue

**Title:** Rotatable Bonds and Virtual Sites Clean-up

## Description

## Description
Rotatable bonds changed to use smirks patterns and removed refs to -geo in README

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [X] Molecule method which finds rotatable bonds.
  - [X] Option to supply different smirks patterns.
  - [X] Tests (removed old ones, added new ones).
  - [X] Removed references to -geo command, since it has been removed from QUBEKit.
  - [X] Rewritten fit() method of v-sites, and somewhat refactored plotting.
  - [ ] Further rework v-sites. Move away from lists of esps and consider breaking up into two classes: one for general maths, one for per-atom fitting.

## Questions
- [ ] Are there other functional groups we want to exclude from rotatable bonds?

## Status
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6595ce76a15e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.