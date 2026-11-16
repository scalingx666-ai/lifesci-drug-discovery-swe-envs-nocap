# Issue

**Title:** fix(trajectory): variable-cell playback — per-frame lattice through detection + CPU/GPU bond paths

## Description

## Problem

NPT / cell-relaxation trajectories rendered cross-cell bonds — and the cell wireframe — with the frame-0 lattice frozen for the whole run. Detection recomputed fractional coords with the wrong inverse, `conn_to_typed_topology` and the object pipeline applied wrong `jimage` offsets, and the GPU path's `uLattice` uniform never updated. Anything with a breathing/tilting cell showed cross-cell bonds drifting off the atoms as playback advanced.

## Fix — one per-frame lattice threaded through all three layers

- **`Trajectory.svelte`** publishes `trajectory_frame_lattice` per frame via a new `stable_frame_lattice` helper: a 9-number compare that returns the *same reference* when the cell is unchanged, so fixed-cell playback stays identity-stable and fires zero downstream re-work. Variable cells hand out a fresh plain-array snapshot (de-proxied for the hot per-bond reads).
- **Detection** (`bond-computation-controller`): `build_trajectory_overlay_structure` + the typed-worker dispatch use the frame's cell for both the `abc` recompute and the overlay's own `lattice.matrix`; the latest-wins pending slot now pairs the pending frame's lattice so a drained re-dispatch uses the right cell.
- **CPU render** (`StructureScene`): frame lattice feeds `conn_to_typed_topology`, the object pipeline, the tail-sync ctx, and the cell wireframe.
- **GPU render** (`BondManagerInstances`): a new `frame_lattice_matrix` prop feeds *only* the `uLattice` uniform + the renderer's lattice getter — the full-resync config effect keeps tracking the static lattice, so a variable cell costs one `mat3` uniform write per frame, not a buffer rebuild.
- Pause writeback carries the paused frame's full lattice object into `current_structure` (exports / info pane / post-pause edits).

## Verification

- 9 new unit tests (`stable_frame_lattice` identity/snapshot semantics + overlay frame-cell abc recompute); full vitest **4544 passing**, `svelte-check` 0 errors.
- Browser: 64-atom NaCl 2×2×2 with a cubic cell breathing 11.28 → 12.41 Å over 40 frames. In-shader bond stats match the file's a/4 nearest-neighbour distance to 6 significant figures at every frame (min_len ×1.09992 at peak), `over_max`/`non_finite` = 0, cell wireframe scales with the atoms.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d4d07c0ea17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.