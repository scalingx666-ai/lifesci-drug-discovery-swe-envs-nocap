# Issue

**Title:** 0.3.9 update feeds: appcast.xml and latest.json

## Description

Publishes the 0.3.9 update feeds for both platforms. Release `v0.3.9` is public with both assets, built from `main` @ `2a6d4c8` (#71); both download URLs answer.

| File | Platform | Source |
|---|---|---|
| `appcast.xml` | macOS (Sparkle) | `generate_appcast` on the notarized, stapled DMG; enclosure length 68915818 = release asset; keeps 0.3.9, 0.3.8, 0.3.7 |
| `ChemDraft_0.3.9_aarch64.md` | macOS release notes | same text as the release's macOS section |
| `latest.json` | Windows (Tauri updater) | `pnpm release:windows-manifest` on the Windows VM ("ChemDraft Windows port", #70); installer 64109931 bytes, SHA-256 `25628012EEE1A79D3F5BE72806519D5605723E94AC8B44C1C75EF0C99EF3D878`, minisign key `7707cfa35d062e59` matches the app's updater pubkey |

After merge: installed 0.3.8 copies are offered 0.3.9. The Windows VM then runs the 0.3.8 → 0.3.9 in-app update test (#70 step 7).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a6d4c8c21af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.