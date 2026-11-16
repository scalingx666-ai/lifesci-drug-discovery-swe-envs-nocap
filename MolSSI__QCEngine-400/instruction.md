# Issue

**Title:** Allow specifying task config via environment and CLI

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This allows for setting the task config (number of nodes, memory, etc) via the CLI and by environment variables.

(I am looking to run more via the CLI than the python interface, for various reasons.)

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Task configuration can now be set via CLI and environment variables

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d18cfda84510`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.