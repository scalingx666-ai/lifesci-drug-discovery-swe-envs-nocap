# Issue

**Title:** add RB Torsion handler plugin

## Description

## Description
This PR adds a plugin handler for SMIRNOFF force fields to handle proper RB torsions which are only added when using QForce.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [x] Add the RB proper Torsion handler
  - [x] Compare energies using XML vs offxml systems
  - [x] Remove old internal torsion code as it is redundant

## Questions
- [ ] Question1

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `411358f93ecd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.