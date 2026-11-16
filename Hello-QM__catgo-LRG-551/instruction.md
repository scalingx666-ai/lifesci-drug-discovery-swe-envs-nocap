# Issue

**Title:** fix(release): normalize packaged legal checks

## Description

## Summary

- exclude only the internal legal-sync ownership sentinel from Android and iOS archive document checks
- normalize PyInstaller archive path separators before Windows sidecar legal verification
- retain the in-flight v1.4.6 iOS recovery workflow hash while trusting the hardened successor

## Root causes

- mobile packagers and Windows PyInstaller may omit the hidden ownership sentinel because it is build state, not a redistributed legal document
- Windows PyInstaller archive listings use backslashes, while the verifier searched only normalized legal/... paths

## Verification

- TDD RED captured both mobile sentinel and Windows archive separator contracts
- 347/347 Node tests passed
- release-rights and legal-distribution verifiers passed
- git diff --check passed
- independent mobile review PASS; all actual legal sources and ACKNOWLEDGEMENT remain mandatory

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ed047ddd02f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.