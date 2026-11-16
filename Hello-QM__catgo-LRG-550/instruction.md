# Issue

**Title:** fix(release): recover iOS and Windows sidecar

## Description

## Summary

- stage the canonical legal bundle before iOS simulator or signed builds
- allow only the immutable v1.4.6 source to be rebuilt by the trusted main iOS workflow
- bind TestFlight provenance to the exact run-head workflow bytes fetched from GitHub
- preserve the immutable v1.4.6 iOS workflow hash alongside the reviewed recovery workflow
- exclude only the internal legal-sync ownership sentinel from sidecar archive document checks

## Root causes

- iOS Tauri bundling failed before compilation because src-tauri/resources/legal did not exist.
- Windows PyInstaller correctly omitted the hidden .catgo-legal-bundle-owned sync sentinel, but the post-build verifier treated it as a user-facing legal document.

## Security boundaries

The split-source TestFlight recovery is limited to v1.4.6, source commit 06c02979b9e917011a63dcbfb09aaad7cfb9430d, main, and the exact reviewed workflow hash. Finalizer and R2 independently fetch the workflow at the run head SHA, verify its allowlisted hash, and bind both proof jobs to that run id/head SHA.

## Verification

- TDD RED reproduced missing iOS legal staging, untrusted split provenance, and sidecar sentinel mismatch
- 345/345 Node tests passed
- release-rights verifier passed: 2 ledgers
- legal-distribution verifier passed: 10 contracts and 27 files
- git diff --check passed
- independent security review: PASS, no Critical/Important

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d59ecf618fe9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.