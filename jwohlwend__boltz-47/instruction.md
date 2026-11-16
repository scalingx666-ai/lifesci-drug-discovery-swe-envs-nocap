# Issue

**Title:** Added support for setting a different msa server url and controlling msa pairing mode from CLI

## Description

setting msa server URL is useful in multiple practical scenarios

- controlling which public msa server to use
- using a private msa server in case of confidential sequences information

this PR adds control over both:
`--msa_server_url`
and
`--msa_pairing_strategy`

with predict docs updated accordingly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e43f9101886e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.