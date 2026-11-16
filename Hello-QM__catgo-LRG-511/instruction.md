# Issue

**Title:** feat(trajectory): default display mode to structure-only

## Description

Opening a trajectory previously defaulted to `structure+scatter`. The scatter pane is secondary for most MD-playback use; default to the structure view and let users opt into the plot via the view-mode button.

No mount site passes `display_mode` explicitly, so the `$bindable` default is the single switch. Verified live: loading a trajectory lands on the Structure view with no scatter rendered.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `003862acf721`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.