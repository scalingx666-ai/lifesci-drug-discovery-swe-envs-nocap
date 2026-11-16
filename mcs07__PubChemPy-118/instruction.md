# Issue

**Title:** Allow using Mozilla certifi package or custom SSL certs

## Description

This PR contains some further tweaks to the changes in #90:

- `certifi` is made an optional dependency, and used if installed. If not, the previous behavior is retained.
- Also adds the option to override certificates with `PUBCHEMPY_CA_BUNDLE` or `REQUESTS_CA_BUNDLE` environment variables.


Supersedes #90

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f61370ab178`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.