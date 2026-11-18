# Issue

**Title:** Symbol tool memory

## Description

Remembers the last selected symbol or charge tool in the toolbar group, showing its icon and using it as the primary action when returning to the group.

Scopes command-icon priority to the Symbol/charge group so other toolbar items retain their own `assetName` icons. Preserves the symbol tests, adds an asset-icon regression test, and bumps the build stamp to `10.11.15.26-codex`.

Validation on Windows:

- `pnpm lint` passed.
- Toolbar and symbol flyout tests passed.
- Full Vitest suite: 6,017 passed, 9 failed, 33 skipped. Failures were eight timeouts and one missing-editor assertion.
- `git diff --check` passed.

macOS and native app behavior remain unverified.

The remembered symbol resets when the app restarts or the toolbar is rebuilt.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7564a95668c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.