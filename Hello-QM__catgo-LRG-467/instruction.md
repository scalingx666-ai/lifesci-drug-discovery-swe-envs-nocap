# Issue

**Title:** fix(viewer): LAMMPS .data drag-in froze for minutes (parser + PBC + fallback chain)

## Description

## Symptom

Dragging `kerogen24_final_150x52x15_330K.data` (11k-atom LAMMPS data file, `Atoms # full`) froze the viewer for minutes with nothing rendered. OVITO opens the same file fine.

## Root cause chain (profiled in-browser + node repro)

1. **Parser**: the column heuristics mis-detected the 10-column `full` layout (`id mol type q x y z nx ny nz`) and read the **trailing image flags as coordinates** → every atom at the origin. The `# full` annotation in the section header was captured but never used. A second bug: `abc` was computed without shifting by the box origin (this box spans x ∈ [-19.9, 239.4]).
2. **PBC image search**: reads every coordinate **through the Svelte $state proxy** in its hot loops — profiled at 104 s self + 84 s proxy `get` traps. The all-at-origin structure additionally exploded images 8× (89,856 sites).
3. **Bond fallback**: a successful WASM run with zero images fell through to the JS path anyway; the JS pair loop on the exploded structure hit **4 GB+ allocation thrash** (node repro OOMs outright) — the "freeze" is a GC storm.

## Fixes (2 commits)

**perf(pbc)** — `extract_plain_geometry`: one proxy pass into `Float64Array`s; both image-search phases loop over typed arrays only; dedup grid stores plain triples. `find_pbc_images_fast` treats a successful-but-empty WASM result as a real answer instead of redoing the search in JS.

**fix(lammps)** — style annotation (`Atoms # <style>`) wins over heuristics (documented column maps for atomic/charge/molecular/angle/bond/full/sphere); trailing integer image flags are stripped before heuristic detection; atoms are shifted by (xlo, ylo, zlo) before computing `abc`.

## Verification

On the reporting file: 11,232 atoms parse with real coordinates (x span ≈ 145 Å matches the 150×52×15 slab), PBC images **116 ms** (was 190 s), JS bond fallback 1.9 s / 5,643 bonds, no OOM. New tests: 10.6k-atom deep-proxied structure completes ~100 ms with bounded proxy reads; image positions verified as integer lattice translations; `full`-with-flags parse regression. Full suite: 4,410 pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6de343e4da94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.