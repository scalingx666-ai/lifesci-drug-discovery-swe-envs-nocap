# Issue

**Title:** fix(release): bind draft finalization to release id

## Description

## Summary
- resolve draft releases through their database ID because the tag REST endpoint hides drafts
- bind every finalizer read, publish, rollback, and compensation mutation to the same release object
- fail closed if the release ID is no longer bound to the requested tag
- apply the same identity checks to both Cloudflare promotion checkpoints

## Root cause
GitHub's REST  endpoint returns 404 for the v1.4.6 draft, so the finalizer and R2 promotion would fail despite complete assets.

## Verification
- RED reproduced in finalizer/R2 workflow tests
- 20/20 targeted workflow tests pass
- 329/329 complete Node script tests pass
- git diff --check passes
- independent security review: PASS

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `741bfdb48d07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.