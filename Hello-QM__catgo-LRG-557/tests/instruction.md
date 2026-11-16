# Issue

**Title:** fix(release): canonicalize Windows updater metadata

## Description

## Summary
- normalize the canonical Windows updater entry only after the complete desktop release matrix succeeds
- bind the canonical entry to the signed NSIS installer URL and signature
- keep R2 backup command substitution free of AWS progress output so promotion receipts receive exact SHA-256 values
- retain the immutable v1.4.6 workflow trust hash while trusting the reviewed current workflow

## Verification
- 331/331 Node release-policy tests pass
- targeted Tauri, R2 promotion, finalizer, receipt, and macOS provenance tests pass
- git diff --check passes
- independent subagent review: PASS

## Live failure evidence addressed
R2 child run 30214587689 failed before root mutation because aws s3 cp progress output polluted the captured digest. The new regression test requires backup downloads to redirect stdout, leaving only the digest in command substitution.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4125b3b89009`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.