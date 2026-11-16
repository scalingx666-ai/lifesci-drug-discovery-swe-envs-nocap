# Issue

**Title:** Goodbye pytest warnings

## Description

Say goodbye to all pytest warnings, once and for all. This is achieved but turning the warnings into errors using the `-W error` mode, requiring us to fix the causing issues. Generally good practice since:
* it finds more issues in our own code base (see changes)
* and also prevents us from running e.g. into deprecated features from third-party code (see changes)

So the PR essentially finalizes the work from #766. In addition, it enables the `--strict` mode.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c863596c1aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.