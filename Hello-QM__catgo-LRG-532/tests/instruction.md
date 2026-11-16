# Issue

**Title:** fix(atoms,bonds): never destroy pending GPU update ranges on renderer sync

## Description

## Summary

Fixes the **supercell atom-vanish** bug reported on app.catgo-ucsd.org (and reproduced on local main): applying a supercell (viewer control or Build tools/LatticePane) left only the pre-growth atom instances visible — e.g. 112 of 448 spheres — while all bonds rendered; toggling Atoms visibility (remount) restored them.

## Root cause

`AtomInstancedRenderer.sync()` / `force_full_resync()` called `clearUpdateRanges()` at sync start. Three.js uploads only the update ranges present at draw time, and Svelte flushes the sync effect 2–3× between draws during a supercell apply — each later sync destroyed the previous flush's not-yet-uploaded gap ranges, so grown slots kept allocation-time zeros on the GPU (radius 0 → invisible) while `mgr.count`/`mesh.count`/CPU arrays were all correct.

**Regressed by #519** (persistent renderers): pre-#519 the mount effect rebuilt the renderer on every version bump, masking the race with full re-uploads.

## Fix

Remove renderer-side `clearUpdateRanges()` — ranges accumulate until Three consumes-and-clears them at draw (overlaps are merged). Same defect fixed at 3 sites in `bond-instanced-renderer.ts`.

## Verification

- New RED→GREEN regression: `tests/vitest/structure/atoms/atom-renderer-growth.test.ts` (fake GPU mirroring Three's upload contract; grown slots must not stay radius-0).
- Suites: structure 1351 passed, trajectory 429 passed; `svelte-check` 0 errors.
- Headless runtime verify on isolated build: 112-atom LiFePO4 → 2x2x1 all 448 atoms immediate, 2x2x2 (896), back to 1x1x1, Atoms toggle, and the LatticePane real-supercell path — all clean, zero console errors.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e597a4d5a72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.