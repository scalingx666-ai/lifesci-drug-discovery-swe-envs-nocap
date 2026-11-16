# Issue

**Title:** Fixes #939 - Visualiser no longer be blank in Jupyter Lab on first load.

## Description

Prior, selecting `gui_style = 'ngl'` in lab resulted in blank interface due to giving the canvas a `0px` width.

Unfortunately I can't get the build to behave - seems to be an issue with type checking - but it should work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d28e3c589023`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.