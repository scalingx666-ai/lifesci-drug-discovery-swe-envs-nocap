# Issue

**Title:** perf(bonds): cylinder-segment LOD — 8 segments during large-system playback

## Description

## Why

Round-5 attribution pinned the trajectory-playback bottleneck as **GPU-bound, not CPU** (per-frame synchronous JS was 0.6ms after the round-4 proxy work). A drawingBuffer 1/16 shrink lifted fps only +46%, so the frame is split between fill (~14ms) and non-fill **vertex/upload work (~28ms)**. The per-bond cylinder dominates that vertex cost: at ~52k half-bond instances a 16-sided cylinder is ~2× the vertices of an 8-sided one.

## What

`bond_lod_segments(n_atoms, playing)`:
- **Large system (>2000 atoms) + playing** → 8 segments
- **Paused, or small system** → 16 segments (full)

Motion hides the facet count; a paused frame is where the eye scrutinises individual bonds, so it gets full quality back. Small systems always render full segments — the GPU isn't the bottleneck there. This is LOD, **not a global downgrade**: no static frame ever loses quality.

The `geometry` `$derived` rebuilds the InstancedMesh only on the **play/pause edge** (`gpu_transform_active` flips). `atom_positions` gets a fresh identity every frame, so its length is read `untrack`ed — the count only matters when the playback flag flips, which re-runs the derived. Tracking it would rebuild the mesh every frame (the exact churn the trajectory fast-path exists to prevent). The rebuild composes cleanly with the existing GPU-mode transition: the mount effect syncs `last_gpu_active`, so the mode-transition effect short-circuits.

## Verification

- 5 new pure-function unit tests (threshold, playing/paused, small/large, degenerate counts); full vitest **4534 passing**, `svelte-check` 0 errors.
- Runtime (20k-atom trajectory): the bond render mesh (count 51784) reads **16 segments while paused** — directly confirmed via scene traversal. The playing→8 transition is covered by the unit tests + the `gpu_transform_active`-driven `$derived` (a pre-existing dev/prod canvas-teardown artifact from failed backend fetches — unrelated to this change, no geometry/mesh errors in console — blocked the direct pixel read of the playing state).

## Follow-up (not in this PR)

impostor-cylinder spike (ray-cylinder in fragment shader, OVITO-style) as an isolated, artifact-debugged experiment — a larger vertex-side win but with real risks (flicker / card-plane artifacts / early-z fill cost) that must be resolved before it touches the live bond renderer.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d4d07c0ea17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.