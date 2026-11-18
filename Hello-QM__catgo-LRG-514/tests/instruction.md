# Issue

**Title:** perf(trajectory): typed-array WASM bond boundary + kill redundant per-frame pipelines (20k-atom playback)

## Description

## Problem

20k-atom streamed trajectory (`dump.traj`, 19968 atoms / ~26k bonds) playback was bond-bound on the main thread. Live profiling showed **three full bond detections per frame** plus three pair rebuilds:

| per frame | cost |
|---|---|
| static pipeline JSON detection ×2 (stampede via structure cascade) | 2 × ~130ms worker + main-thread JSON parse/convert |
| TrajectoryBondCache JSON detection + prefetch bursts | ~130ms each + 20k-site structure clone |
| trajectory fast-path detection (JSON) | ~130ms + 13ms stringify + 50ms serde parse |
| `build_trajectory_bond_pairs` ×3 | 122–136ms each (52k radii dict lookups/frame + alloc churn) |

## Changes

1. **ferrox typed entry** (`detect_bonds_radii_typed`): Float32Array positions + Uint8Array atomic numbers + flat lattice/pbc in, `BondTable` (pairs u32 / images i8 / lengths & strengths f32) out. No serde JSON on either side. Node parity smoke vs `detect_bonds_radii`: identical bond sets incl. cross-boundary images (PBC crystal + lattice-less molecule).
2. **Worker boundary**: new `bonds_typed` message with transfer lists both directions; positions copied before transfer (caller keeps ownership). Falls back to the JSON path on worker failure / exotic species / non-atom_radii strategies.
3. **Dispatch routing**: `dispatch_traj_async` picks the typed route when the effective strategy is atom_radii (always true above the 8k solid_angle downgrade); overlay-structure build is now lazy (JSON fallback only). Same self-image starburst filter as `wasm_bonds_to_pairs`.
4. **Static pipeline gate**: StructureScene's bond `$effect.pre` now early-returns while `trajectory_frame_positions` streams — it was clearing `bond_connectivity` and re-detecting every frame in parallel with the fast path. Variable-N trajectories (positions === null) keep the slow path — it is their only bond source.
5. **Dead pipeline removed**: `TrajectoryBondCache` wiring in Structure.svelte computed per-frame connectivity + prefetch whose only sink was a prop **nothing reads**. Wiring + prop removed; module & unit tests left for a follow-up deletion.
6. **Pair-rebuild optimization**: per-bond stale thresholds memoized (per-site radii keyed on sites identity — one ~30ms Svelte-proxy scan per trajectory; thresholds per connectivity identity); `compute_bond_transform` rewritten allocation-free (same output, covered by existing 28 bonding tests).

## Measured (live, 20k atoms, Chrome dev build)

- Bond detection per frame: 3 full JSON computes → **1 typed compute, ~50ms off-thread** (JSON path wasm was ~130ms + ~65ms boundary tax)
- `build_trajectory_bond_pairs`: 122–136ms → **15–29ms** (typed-conn pass; node micro-bench 35.2→17.1ms for the pure loop)
- Boundary tax: ~55ms serde+JSON.parse → **~0.4ms** typed-array getters
- Static-pipeline stampede and `bond_connectivity = []` churn: **gone** (console-verified)

## Not fixed here (follow-ups)

- Playback fps at 20k atoms is now dominated by the **per-frame structure cascade** (Svelte proxy traversal `get`/`proxy` ≈ 8s + GC 3.8s per 25s trace window, plus dev-mode `get_stack` tracing) and streamed-chunk fetch — tracked separately with the trace file.
- Delete `trajectory-bond-cache.svelte.ts` + its tests once confirmed no consumer reappears.
- First rebuild per frame (interim render with previous connectivity) still ~180ms in dev — suspected proxy/GC, revisit on a prod build.

## Tests

- Full vitest: 4496 passed / 0 failed (one unrelated flake on a prior run, green on re-run)
- svelte-check: 0 errors
- New: `tests/vitest/structure/trajectory-bond-pairs.test.ts` (9 cases: stale filter, jimage geometry, tolerance/sites cache invalidation, typed→conn conversion, Z-array memoization)
- cargo check --features wasm: 0 errors; wasm pkg rebuilt with wasm-pack

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2020cd94c09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.