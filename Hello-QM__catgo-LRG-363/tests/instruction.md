# Issue

**Title:** fix(structure): normalize ortho pan speed to camera distance

## Description

## Problem
Panning a non-periodic system (small molecule) felt much slower than a periodic cell for the same mouse drag — a sensitivity issue, not fps.

## Root cause
`TrackballControls._panCamera` scales on-screen pan by `_eye.length()` (camera→target distance). For the ortho camera the `1/zoom` term cancels against the projection's `×zoom`, but `_eye.length()` has **no** such cancellation. CatGo places the ortho camera at a distance that scales with structure size, so molecules (close camera) panned slowly and cells (far camera) fast. Rotate uses `_rotateCamera` (pixel-angle only) and was never affected.

`compute_structure_size` can't serve as a proxy — it returns a flat `10` for lattice-less (non-periodic) systems, so it doesn't track the real distance.

## Fix
Read the true eye length at drag start (`onstart`) and set `panSpeed = pan_speed × PAN_REF_EYE / eye`, making on-screen pan ∝ `pan_speed` for every structure. Perspective pan already tracks the cursor 1:1, so it's left alone. (+18 lines, one file.)

## Test
Verified by hand on a small molecule vs a large crystal — pan now feels identical. `pnpm check`: 0 errors.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f1cba105e14`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.