# Issue

**Title:** Match CLI behavior for boolean GIF rotation

## Description

Updates the Python GIF API so `gif_rot=True` uses the default y-axis, matching the CLI’s bare `--gif-rot` behavior. Explicit axes and disabled rotation continue to behave as before.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6802a375e337`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.