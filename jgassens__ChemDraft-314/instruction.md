# Issue

**Title:** Publish 1.1.1 update feeds (merge only at publish)

## Description

**Do not merge until the owner publishes the v1.1.1 release.** Merging points every installed 1.1.0 at 1.1.1.

- `appcast.xml`: new 1.1.1 entry from generate_appcast (signed); the DMG on the draft release is the exact notarized file (80,258,542 bytes).
- `release-notes/macos/ChemDraft_1.1.1_aarch64.md`: the macOS notes the update window shows.
- `latest.json`: from the windows-release run 42511059635 at 6be9bb8e, with the Windows notes added; the release asset and SHA256SUMS.txt were updated to match.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6be9bb8eb040`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.