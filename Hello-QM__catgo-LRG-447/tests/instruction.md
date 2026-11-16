# Issue

**Title:** fix(release): macOS Developer-ID signed-only (disable flaky notarization)

## Description

Apple notarization hung 2-3h on the runner twice for v1.4.1 (240MB backend → hundreds of nested binaries + flaky long-poll → -1009). Ship macOS **Developer-ID signed** (first launch right-click → Open); notarization is a follow-up. Win/Linux unaffected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93ea425b49ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.