# Issue

**Title:** fix(server,viewer): streamed trajectory frames carry the cell + Compute-bonds banner receives real clicks

## Description

Two fixes discovered while chasing the same user report (20k-atom `dump.traj` playback: bonds missing, laggy, 'Compute bonds' button dead).

## 1. Backend: `_atoms_to_frame` dropped `atoms.cell` (the big one)

Every streamed `.traj` / `.lammpstrj` frame reached the viewer **lattice-less** (the landing-page Open File streams files >20MB through the backend). Downstream, ferrox-wasm treats a lattice-less structure as a molecule (`pbc=[F,F,F]`), forcing the O(N²) brute-force neighbor path instead of the cell list:

| | pbc | in-wasm detect (19968 atoms) |
|---|---|---|
| before | `[false,false,false]` | **3790–4321 ms** |
| after | `[true,true,true]` | **45–66 ms** (~70×) |

Native bench for reference: cell-list 75ms vs pbc-off 4.8s at 19683 atoms. Cross-cell bonds were also wrong without the cell. XDATCAR had its own reader that already emitted `lattice`; `.traj`/LAMMPS-dump now match. Emitted only for periodic, non-degenerate cells — molecules stay lattice-less. +3 backend tests.

## 2. Viewer: Compute-bonds banner never received real mouse clicks

The bonds-deferred banner (#507) was portaled into `threlte.dom`, whose canvas-area wrapper has `z-index:0` (own stacking context) — the banner could never stack above the atom legend (`z-index:1`, direct child of `.structure-main`). Where the two overlapped, every real click landed on the legend LABEL; programmatic `.click()` bypasses hit-testing, which is why it 'worked' in automation but not for the user. New `interactive_overlay_portal` mounts interactive overlays on `.structure-main` (sibling of the legend); banner raised to z-index 10. Verified via `elementFromPoint`: LABEL before → BUTTON after.

## Diagnosis trail

Native bench → staged in-wasm timings → worker-payload probe (`keys=[sites]`) → `console.trace` → `App.svelte stream_file_if_large` → `remote-frame-loader` (frontend lattice passthrough was already correct; the backend simply never sent one).

Pairs with #510 (playback fast-path) — together they take the 20k case from 'bonds flash every ~10s, seconds-long stalls' to bonds-every-frame at interactive rates.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `003862acf721`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.