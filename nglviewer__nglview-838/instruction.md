# Issue

**Title:** Gridbox enhancement

## Description

- add `handle_resize` for backend and `handleResszie` for frontend: The idea is that we can properly resize the view's container if the view is in nested boxes.
- add EXPERIMENTAL Fullscreen class to handle fullscreen.
- Add syncing repr between two views of two models (I am not sure about this usage).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe9cfcec2c61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.