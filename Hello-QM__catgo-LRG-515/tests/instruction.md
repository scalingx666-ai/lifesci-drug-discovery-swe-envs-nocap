# Issue

**Title:** perf(ferrox): generalize cell-list neighbor search — no more O(n²) fallback (FFF 1.9s → 24ms)

## Description

## Problem

`build_neighbor_list` only took the O(n) cell-list path for fully periodic systems whose cell heights all exceed the cutoff; everything else — molecules / LAMMPS xyz dumps (pbc FFF), slabs with an open axis, cells thinner than the cutoff — silently fell back to O(n²) brute force. At 19683 atoms that's **1.9s per bond detection vs 33ms** for the periodic twin (native; the wasm viewer path is correspondingly worse).

## Approach (OVITO `CutoffNeighborFinder`)

- **Periodic axes** bin the wrapped cell `[0,1)`. Atoms are wrapped in with their integer shift recorded; emitted images are corrected back (`I = m − s_j + s_i`) so results refer to the original unwrapped coordinates.
- **Non-periodic axes** bin the atoms' actual fractional extent (a molecule in a huge bounding box only bins the occupied region); stencil offsets leaving the grid are skipped — clamp, no ghost atoms.
- **Stencil** spans `⌊cutoff/bin_height⌋+1` bins per axis, precomputed once: a periodic axis thinner than the cutoff naturally yields multi-image neighbors (|image| ≥ 2) instead of forcing brute force. Each stencil offset maps to a unique (bin, image) pair — no duplicates by construction. Per-axis bin counts cap at ~2·∛n so sparse gases don't allocate absurd empty grids.
- Dispatch: cell list for every system above `cell_list_threshold`; brute force remains only for small systems (doc note added: it assumes near-in-cell coordinates — its ±max_images window undercounts far-unwrapped inputs, which the cell list handles exactly).

Both rayon and serial paths now share one `CellList::neighbors_of` kernel.

## Numbers (native, 19683 atoms, cutoff 5 Å, `examples/bench_bonds.rs` — committed)

| case | before | after |
|---|---|---|
| pbc FFF | 1.9 s (brute force) | **24.1 ms (~79×)** |
| pbc TTT | 33.3 ms | 29.1 ms |

Bond counts identical on both paths (20850 / 19999).

## Tests

6 new cell-vs-brute parity suites comparing exact `(center, neighbor, image, distance)` multisets: non-periodic molecule, mixed-pbc slab with vacuum, thin-cell multi-image (asserts |image| ≥ 2 pairs occur), unwrapped coordinates (reference = brute force on a wrapped twin with images transformed back — brute force itself undercounts there), skewed triclinic, sparse-gas capped grid. Full ferrox suite: **1062 passed**. `cargo check --features wasm` clean.

Independent of #514 (different files); both stack on main.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2020cd94c09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.