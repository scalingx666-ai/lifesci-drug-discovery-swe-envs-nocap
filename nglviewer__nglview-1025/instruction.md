# Issue

**Title:** FIX: displaying view multiple times with shape + UPGRADE NGL version

## Description

<img width="579" alt="image" src="https://user-images.githubusercontent.com/4451957/175864607-a0f9d49e-c66d-4b37-9b23-29e71464ceb9.png">

Fix 
FIX #1013

Without the fix, the 2nd (buffer) component will be `undefined` because it does not exist yet: https://github.com/nglviewer/nglview/blob/b1d50de25672a3849ec2d0feb770c73f14de7b27/js/src/widget_ngl.ts#L573

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `22a19c58a597`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.