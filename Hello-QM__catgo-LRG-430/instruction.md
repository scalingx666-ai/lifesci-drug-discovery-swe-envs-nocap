# Issue

**Title:** fix(release): wire macOS notarization via App Store Connect API key

## Description

v1.4.0 shipped macOS **unsigned** because tauri-action's Apple-ID/app-specific-password notarization path 401'd — those secrets don't exist. The repo's Apple creds are **App Store Connect API-key** based (`APPLE_API_KEY_ID` / `APPLE_API_ISSUER_ID` / `APPLE_API_KEY_P8`, already used by `ios-build.yml`).

This writes the `.p8` to a file on the macOS runner and passes `APPLE_API_ISSUER` / `APPLE_API_KEY` / `APPLE_API_KEY_PATH` to tauri-action (plus the Developer-ID signing cert + `APPLE_DEVELOPMENT_TEAM`). No-op on Windows/Linux.

**Caveat to verify on the build**: notarization requires a **Developer ID Application** cert. If the repo's `APPLE_CERTIFICATE` is an *Apple Distribution* cert (iOS/App-Store type), the macOS build will fail and a Developer ID cert must be added. The `v1.4.0` tag was moved to this commit to test it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4216160c24ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.