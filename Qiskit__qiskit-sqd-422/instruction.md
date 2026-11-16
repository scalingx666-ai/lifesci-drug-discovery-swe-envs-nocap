# Issue

**Title:** Split dependency install out of the "Show the installed qiskit" step

## Description

`tox -e py --notest` installs the whole dependency graph, so a dependency that fails to build is reported against a step named for printing a version number. On #420 an h5py build failure surfaced that way, with "Test using tox environment" skipped.

No behavior change; the same two commands run in the same order.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67b7ebd11ac3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.