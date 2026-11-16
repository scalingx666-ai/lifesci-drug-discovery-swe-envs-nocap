# Issue

**Title:** fix(viewer): rotate selected atoms about screen axes, not cell axes

## Description

## Problem

Rotating **selected atoms** in the structure viewer rotated them about the **cell** XYZ axes instead of the **screen** XYZ axes. Reported by user: 旋转选中原子时轴是晶胞XYZ而非屏幕XYZ。

## Root cause

The rotation screen frame is built from `camera.quaternion` (**world** space), but the rotation is applied to `structure.sites.xyz`, which are **local/cell** coordinates. Atoms render inside `<T.Group {rotation}>` (`StructureScene.svelte`) where `R_group = Euler(scene_props.rotation, 'XYZ')`. The code omitted `R_group⁻¹`, so the world screen axis was applied directly to local coordinates.

Pure camera-orbit keeps `scene_props.rotation = [0,0,0]` (fix is a no-op there, matching prior correct behaviour). But reorienting the structure via the **group** rotation makes `R_group ≠ I`, and then atoms rotate about the cell axes. Triggered by:

- pressing `r` (lattice align, `interaction.svelte.ts:1070`)
- axis-lock X/Y/Z + drag (`:1313`)
- the numeric rotation controls (`StructureControls.svelte`)

## Fix

New pure helper `world_axis_to_local(axis, group_rot)` in `rotation-math.ts` maps the world screen axis into the local frame via `R_group⁻¹` (conjugation `R⁻¹·Rot(a)·R = Rot(R⁻¹·a)`), matching the existing `local_to_world` convention. Applied on **both** the drag (`:1514`) and keyboard (`:790`) rotation paths. Also corrects the yellow axis indicator (rendered inside the rotated group).

## Tests

- +4 vitest in `rotation-math.test.ts`: identity no-op regression, +90° z inverse, round-trip, unit-length. Suite **15/15 green**.
- `svelte-check`: 12 pre-existing errors (all unrelated files), zero in touched files — no regression.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eef8a5e1c44f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.