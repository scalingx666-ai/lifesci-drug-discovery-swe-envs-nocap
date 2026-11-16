# Issue

**Title:** perf(bonds): right-size GPU topology attrs — 12MB → ~1.25MB at 52k instances

## Description

## Problem

The GPU vertex-transform bond path (#524) allocated its three static-topology attributes — `a_site` (vec2 f32), `a_jimage` (i8×3), `a_half` (f32) — eagerly at *mesh capacity* (1M instances, ~12MB CPU+GPU combined) on the first GPU-transform sync, even for a ~50k-instance system.

## Fix

Lazily size the three attrs to the live instance count with 2× growth headroom (floor 1024 instances, clamped to mesh capacity). At a typical 52k instances that's ~1.25MB instead of ~12MB — ~90% off.

- Growth swaps in fresh `InstancedBufferAttribute`s via `setAttribute` (a WebGL instanced attribute can't grow in place — the renderer keys its GL buffer on the attribute object). No data copy: `sync_gpu_topology` full-rewrites `[0, count)` immediately after, and a fresh attribute uploads its whole array on first render regardless of update ranges.
- Steady-state playback re-syncs hit a two-compare early return every frame — capacity only grows, never shrinks, so reallocations are O(log n) over a renderer's lifetime.
- `kind`/`color`/`opacity` attrs stay mesh-capacity-sized (shared with the CPU path's scattered dirty-slot writes) — a separate cut if ever needed.

## Verification

23/23 in `tests/vitest/structure/bonding/` (existing 7 GPU-topology tests + 2 new: initial right-size, data-intact-after-growth), `svelte-check` 0 errors.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d4d07c0ea17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.