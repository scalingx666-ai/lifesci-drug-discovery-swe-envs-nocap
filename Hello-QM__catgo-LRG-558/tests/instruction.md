# Issue

**Title:** fix(release): reconcile R2 versioned assets

## Description

## Summary
- run a second non-deleting R2 sync so same-key upload/delete races cannot leave required files missing
- HEAD-probe every required public asset and exact Content-Length before the 2.41 GB byte-for-byte verification pass
- preserve the full receipt/hash verification gate after availability checks

## Live evidence
Run 30214826974 logged upload of CatGo_1.4.6_amd64.deb followed by deletion of the same key in one aws s3 sync --delete operation. The DEB became the only 404 while all other required assets matched exact sizes.

## Verification
- RED regression reproduced both missing reconciliation and missing fail-fast probe
- targeted R2/finalizer tests: 21/21 pass
- complete Node release-policy suite: 331/331 pass
- git diff --check passes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fbe22a22f14`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.