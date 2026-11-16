# Issue

**Title:** iboview: workaround for qt issues on wayland

## Description

IboView does not work properly on wayland and produces graphic glitches that make it unusable. By setting `QT_QPA_PLATFORM=xcb` we can force xwayland usage, under which IboView behaves correctly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c42d06ff872`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.