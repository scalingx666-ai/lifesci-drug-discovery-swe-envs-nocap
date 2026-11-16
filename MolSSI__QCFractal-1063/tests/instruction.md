# Issue

**Title:** Remove unused worker_timeout config option

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Very simple - the qcfractal server had an option "worker_timeout" that was used when we depended on gunicorn.
We don't use gunicorn anymore, and this has had no effect for a while. So remove the option (with a deprecation warning for anyone who might have it set).

(This option deals with gunicorn web workers, not compute workers)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f5296848b26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.