# Issue

**Title:** perf(trajectory): cut the per-frame reactive cascade during 20k-atom playback

## Description

> Reopened from #516 — GitHub auto-closed it when its stacked base branch (`feat/traj-typed-array-bonds`, #514) was merged and deleted. Rebased onto main, content unchanged.

**Stacked on #514** — merge that first, then rebase this onto main (or merge #514 into main and retarget).

## What

Trace-guided elimination of per-frame reactive work during streamed fixed-topology trajectory playback. A CPU profile showed the main thread with zero idle: Svelte proxy traversal + GC dominated, none of it bond *computation* (that was fixed in #514).

Cuts (each anchored to a profiled hot chain):

1. **MCP push effect gate** (Structure.svelte) — `bridge_structure` (= current frame's structure) churns identity every frame; `JSON.stringify` deep-walked a 20k-site `$state` proxy per frame (~300k proxy traps + multi-MB throwaway string — the single largest cost, ~4s per 25s window in dev). Gated while `trajectory_frame_positions` streams; teardown re-fires and pushes final state; the 5s MCP heartbeat still covers listeners.
2. **AtomManager positions batch** — `set_position` bumped the reactive `#version` `$state` once **per atom** (20k reactive writes/frame from the position-write loop; 3.8s of dev stack-capture alone). New `begin/commit_positions_batch` (same pattern as colors/opacities); one bump per frame.
3. **manifest_formula memoized** on structure identity (was two full proxied site walks per frame via the manifest-refresh effect; frozen structure → O(1), doping trajectories swap identity → recompute correctly).
4. **compute_atom_span_radius memoized** on structure identity (was recomputed per rendered frame by the depth-cue task).
5. **atom_positions_buffer** skips the proxied `sites[]` base-fill during playback when the manager covers every site.
6. **visible_bond_pairs fast paths** — skip ~52k `is_site_visible` proxy reads/frame when nothing hidden, deleted-key strings when nothing deleted, manual-merge set when no manual bonds; `Float32Array.some(closure)` → plain loop.
7. **Numeric bond keys** (`pack_bond_key`, float64-exact packing with string fallback) for `slot_to_filtered_idx` and the bond_manager shadow-sync diff — was ~100k short-lived key strings per frame, a large share of the 4-5s/25s GC.
8. **Bond hitbox rebuild throttled** to 500ms during playback (was 2×26k Matrix4 rebuilds per frame for hover picking nobody can use while atoms move), with a trailing rebuild so picking settles correct after pause.
9. **Bug fix: latest-wins drain never published.** `dispatch_traj_async`'s resolve only wrote `bond_connectivity` when no newer frame was queued — during continuous playback one always is, so the visible connectivity stayed frozen at the pre-playback detection for the whole run while the stale filter silently dropped hundreds of moved bonds per frame. Resolve now always publishes the freshest connectivity before draining.

## Measured (dev build, 20k-atom streamed dump.traj, same box)

- Playback: 0.27 fps (pre-#514) → ~0.5–1.1 fps (high run-to-run variance from streaming-chunk timing). Not "flight" yet — see below.
- Dev-only Svelte stack-capture (`get_stack`) eliminated from the profile after the positions batch.
- Bond correctness: connectivity now updates each resolve instead of freezing at frame 0.

## Remaining bottleneck (next task, precisely located)

The bond render chain rebuilds ~26k `BondPair` objects per frame and re-diffs them through `visible_bond_pairs → filtered_bond_pairs → slot_to_filtered_idx → bond_manager mirror` twice per frame. The structural fix is typed-connectivity straight into the instanced buffers (revive the deferred "render side consumes typed table" task). Also worth benchmarking a production build — dev-mode proxy interceptors inflate every remaining site read.

## Tests

Full vitest 4496 passed / 0 failed; svelte-check 0 errors. Live-verified on the 20k dump.traj (bond counts now track per frame; no visual regressions on the water demo / static structures).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d525d6524fff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.