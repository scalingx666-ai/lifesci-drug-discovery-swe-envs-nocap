# Issue

**Title:** update torsiondrive to use task config

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR updates the torsiondrive procedure to use the new `task_config` argument which will stop warnings when running torsiondrives, .

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
The torsiondrive procedure now uses `task_config` internally.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ ] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1822ea441744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.