# Issue

**Title:** fix(release): grant draft visibility to validators

## Description

## Summary
- grant contents write only to jobs that must read/download a GitHub draft release
- keep the workflow default and Cloudflare dispatch job read-only
- enforce that validation and mirror code contain no GitHub release create/edit/upload or release POST/PATCH/DELETE commands

## Root cause
GitHub hides draft releases from a GITHUB_TOKEN without push-equivalent repository access. Finalizer run 30214089726 used contents read and failed with release not found before any mutation. The same resolver succeeded in the iOS attestation job with contents write.

## Verification
- RED reproduced in permission boundary tests
- 20/20 targeted finalizer/R2 tests pass
- 329/329 complete Node script tests pass
- failure occurred before Cloudflare promotion or publication
- independent security review: PASS

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a97a67786a1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.