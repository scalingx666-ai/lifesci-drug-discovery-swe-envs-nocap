# Issue

**Title:** fix(docs): Render header button uses the accent color (looked disabled)

## Description

: the Render toggle inherited bare `.editor-btn` styling — muted gray that reads as disabled next to blue Visualize / green Save. New `.action-btn` class shares the Visualize accent styling.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0959185a9824`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.