# Issue

**Title:** Add unit tests

## Description

* Add 'seed' option to command line to help with reproducibility.

* Add some consistency tests for chunking

* Add some regression tests, covering:
    - Input embedder
    - Relative position embedder
    - Structure output

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc6993fbfb55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.