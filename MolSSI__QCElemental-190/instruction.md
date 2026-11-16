# Issue

**Title:** try minimal storage mol for atomic_number

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Start of minimal storage for mol. Minimal validation is definitely a target, but I understand minimal storage is first. I started passing up the defaulted fields up but then figured why bother passing when it can be computed as needed. This is a first stab at #169 dealing only with atomic_number. Autogeneration does work or the nuclear_repulsion_energy fn test would fail. Currently 12 tests fail, mostly with extra_fields/serialization trouble. Looking for first comments.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8904f1c9c63b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.