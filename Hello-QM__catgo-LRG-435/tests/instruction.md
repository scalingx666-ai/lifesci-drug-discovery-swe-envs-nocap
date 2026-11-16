# Issue

**Title:** fix(release): decouple macOS signing secret from iOS (MACOS_* not APPLE_*)

## Description

macOS desktop and iOS pipelines both read `APPLE_CERTIFICATE/_PASSWORD/_SIGNING_IDENTITY` but need different cert **types** (Developer ID Application vs Apple Distribution). Point macOS signing at new `MACOS_*` secrets so the two no longer collide. `APPLE_DEVELOPMENT_TEAM` + `APPLE_API_*` (notarization) stay shared.

Requires new repo secrets `MACOS_CERTIFICATE` / `MACOS_CERTIFICATE_PASSWORD` / `MACOS_SIGNING_IDENTITY` (Developer ID cert), and `APPLE_CERTIFICATE` restored to the iOS Apple Distribution cert.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1264ca877da2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.