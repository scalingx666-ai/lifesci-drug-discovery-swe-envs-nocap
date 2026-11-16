# Issue

**Title:** Updated docstrings and function annotations for compute and compute_procedure

## Description

<!-- Thank you for your contribution! -->

## Description
 

Still waiting on comment re: updating `local_config` -> `task_config` but wanted to provide these updates before I forgot.

## Changelog description
Updated docstrings and function annotations for compute and compute_procedure. Renamed kwarg `local_config` -> `task_config` to more clearly express that passed options become a `TaskConfig` argument.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x ] Code base linted
- [ x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dafd9748465a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.