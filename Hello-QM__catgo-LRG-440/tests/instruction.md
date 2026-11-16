# Issue

**Title:** fix(vscode-ext): stop main-thread solid_angle per trajectory frame (jank)

## Description

## Problem
Trajectory playback is janky **only in the VS Code extension, only with the `solid_angle` bonding strategy** (`atom_radii`/`electroneg_ratio` are smooth; desktop & web are smooth even with `solid_angle`).

**Root cause:** bond connectivity is recomputed every trajectory frame; `solid_angle` is the heavy WASM kernel and runs materially slower in the VS Code webview WASM runtime than on desktop (Tauri/JSC), saturating the main thread. Console proof during playback: `[bonds] Main WASM | solid_angle | 625 atoms | ...` flooding every frame.

Ruled out along the way: 1 GB streaming threshold, bond-worker CSP, software WebGL (renderer is real RTX 4060 / ANGLE), rAF throttling (ext & matterviz both rAF≈4 ms), V8 Liftoff/sync-instantiate, per-frame host IPC (message count = 0).

## Fix
- **Extension-only `solid_angle → atom_radii` downgrade for trajectory frames**, applied to **both** bond paths:
  - fast path `compute_bond_connectivity_for_frame` (constant-N, has `position_cache`),
  - **slow path `compute_bond_connectivity` (variable-N)** — the reported file is variable atom-count (581–669), so it has no `position_cache`, `trajectory_frame_positions` is `null`, the fast branch is skipped, and the slow path is what actually runs. Gated by a new `is_trajectory_frame` param (StructureScene passes `trajectory_step_idx >= 0`).
  - Strictly gated on `__CATGO_VSCODE_EXTENSION__ && is_trajectory_frame` → **desktop/web byte-identical**; static structures in the extension keep the user's `solid_angle`.
- **Frame-connectivity cache `TRAJ_FRAME_CACHE_MAX` 32 → 512** so a full trajectory stays cached across loop/scrub (316-frame trajectories were a perpetual cache miss → recompute every frame).
- **never-bonds leak fixed:** `wire_trajectory_bond_cache` dispatched `compute_bonds_async(solid_angle)` every frame + prefetch ±5 **even when `show_bonds === 'never'`**, feeding an unread/dead prop (`trajectory_bond_connectivity`). Now gated on `show_bonds !== 'never'`.

## Verification
- `pnpm check`: baseline-equal (11 pre-existing errors in unrelated files, **0 new**).
- `pnpm exec vitest run tests/vitest/trajectory tests/vitest/structure`: 1657 pass, no regressions.
- New tests: trajectory bond scheduling, ext `solid_angle` downgrade (fast + slow path), never-gate.

## Notes
- **Must rebuild/repackage the extension to test** — the installed `.vsix` bundles a prebuilt `webview.js`, and the downgrade only activates in the extension build (`__CATGO_VSCODE_EXTENSION__`).
- Residual (out of scope): variable-N `never` jank floor = non-bond per-frame `current_structure` cascade + instanced-mesh rebuild (no `position_cache` for variable-N). Tolerable today; a future fix would build a position cache for variable-N trajectories.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `119c70fe5977`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.