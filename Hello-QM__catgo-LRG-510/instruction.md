# Issue

**Title:** fix(trajectory): keep bonds visible every frame on indexed/streaming trajectories

## Description

## Problem

Playing a large trajectory (e.g. 300MB / 1600-atom / 5000-frame LAMMPS `dump.xyz`) showed bonds only every few frames, irregularly.

## Root cause

Files over the 50MB text threshold (`MAX_TEXT_FILE_SIZE`) load via `load_with_indexing` → `frame_loader` attached → `position_cache` disabled → Architecture P fast-path off. Playback fell into the slow path: `current_structure` rewritten every frame, re-entering the **static** bond pipeline, whose generation counter drops nearly every in-flight worker result during playback (worker ~30-40ms vs frame advance). Bonds only rendered on frames where the worker won the race. Console evidence: zero `[bonds-traj]` logs during playback; 35+ worker completions vs ~5 `build_bond_pairs` in 6s.

## Fix

Extend Architecture-P-style playback to indexed trajectories with constant topology:

- New `src/lib/trajectory/frame-positions.ts`: memoized per-frame `Float32Array` builder (LRU-capped at 512 frames ≈ 10MB @1600 atoms). Stable array reference per frame index keeps the bond frame-connectivity cache (`frame_conn_cache`, keyed by reference) valid on scrub-back / looped playback.
- `Trajectory.svelte` slow path: constant-topology frames feed `trajectory_frame_positions` (+ forces when present) and leave `current_structure` static → the scene's trajectory bond fast-path (frame cache + latest-wins async + stale-render) keeps bonds visible every frame.
- Variable atom counts, `force_slow_path` sources (element-swap frames), and pending edit ops keep the old per-frame structure-write path; the memo cache clears on any trajectory identity change.

## Verification

- Live against the 300MB dump.xyz: `[bonds-traj]` dispatch cadence, `build_trajectory_bond_pairs` on **every** frame (~1700-2050 pairs), stale-filter dropping only single-digit stretched pairs, bonds visible throughout playback (screenshot-verified mid-play at frame 230/5000).
- `tests/vitest/trajectory`: 420 passed; +6 new unit tests for the frame-position cache.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `003862acf721`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.