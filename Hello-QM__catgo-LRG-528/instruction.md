# Issue

**Title:** perf(trajectory): exempt the trajectory container from Svelte's deep $state proxy

## Description

> Stacked on #526 (variable-cell lattice). Review/merge #526 first; this branch's diff is only its own commit.

## Problem

Playback traces after #524 showed the remaining main-thread CPU dominated by Svelte proxy `get` traps (~6% scripting) and GC of proxy wrappers (~9% GC share). The trajectory object lives in a deep `$state`/`$bindable`, so every `frames → structure → sites` read during playback (position-cache builds, `frame_pos_cache` first laps, the `current_frame` effect) paid per-property proxy traps over 20k-atom frames.

## Fix

Svelte only deep-proxies plain objects and arrays (its `proxy.js` prototype check). `mark_raw_trajectory()` re-prototypes the trajectory container onto a marker prototype, so the whole tree escapes proxying even inside a deep `$state` — which also sidesteps `$bindable` having no `$state.raw` variant. Every intentional mutation already flowed through explicit top-level reassignment, so reactivity is unchanged:

- all 9 assignment sites in `Trajectory.svelte` mark the container (2 loads + 7 spread-refreshes / `refresh_after_external_edit`);
- `plot_metadata` adoption becomes a top-level spread-reassign — it was the single genuine deep-write dependency (streamed-load plot population);
- `frame_loader` attaches before publish instead of relying on a same-tick post-assignment write;
- `MobileWorkspace` / `StructureEditModal` trajectory owners → `$state.raw` (wholesale assignment only), matching the already-raw `WorkflowEditor` / `EngineTaskEditor` owners;
- runtime tests pin the exemption against the real `$state` runtime, with an unmarked-POJO control that fails loudly if Svelte ever changes proxy semantics.

## Verification

Full vitest **4544 passing** (4 new raw-container runtime tests), `svelte-check` 0 errors.

Prod build (48MB / 20k-atom / 100-frame `.traj`, scrubber-driven cached-lap benchmark): cached lap **27–28 fps** vs the #524 baseline of 23.8 avg — **+17%**. The vsync-uncapped ceiling (microtask-yield, no rAF wait) is 63 fps, so the frame-supply chain (~15.8 ms/frame), not vsync, is the next bottleneck.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d4d07c0ea17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.