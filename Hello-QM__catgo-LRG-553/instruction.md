# Issue

**Title:** fix(release): detect draft iOS release

## Description

## Summary
- query draft releases through gh release view so v1.4.6 is visible before publication
- bind the exact recovery workflow hash in the release trust policy
- keep the immutable tag workflow hash trusted while removing failed intermediate hashes

## Root cause
The signed iOS build and TestFlight upload succeeded, but the attestation job used the REST tag endpoint, which returns 404 for draft releases.

## Verification
- 347/347 Node tests pass
- release-rights verifier passes for both ledgers
- legal verifier passes 10 contracts / 27 files
- git diff --check passes
- independent review: PASS

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e6c558c4a6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.