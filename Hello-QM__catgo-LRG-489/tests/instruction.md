# Issue

**Title:** fix(viewer): depth cueing no longer washes out molecules

## Description

## Bug
H₂O / small molecules render **washed out / greyed** — the whole molecule looks faded.

## Root cause
Depth-cue fog range was computed from `compute_structure_size(lattice)` = the **cell** size. A molecule sits in a large vacuum box, so the fog interval spanned the entire box while the atoms occupied only its centre. The whole molecule therefore fell *inside* the fog interval (after `depth_cue_start`) and got mixed uniformly toward the background colour.

Confirmed live on the Water demo: fog `near = 9.9`, nearest atom at `10.9` → every atom past the fog start, uniform ~7-10% grey wash. Turning depth cueing off removed it entirely (pixel mean\|Δ\| 3.3).

## Fix
New pure helper `compute_atom_span_radius(structure)` — half the largest atom bounding-box axis, i.e. the **actual drawn extent**, independent of vacuum padding. Fog `half_range` uses it instead of the lattice size (falls back to the lattice only when there are no atoms; floored at 0.1 Å so the interval never collapses).

- **Crystals** (atoms ≈ cell): unchanged — TiO₂ still fades back rows (fog on/off differ ~40%).
- **Molecules**: only genuine front-to-back depth cueing remains, no flat wash. Water now matches depth-cueing-off (pixel mean\|Δ\| **0.24** vs 3.3 before).

## Tests
- New `compute_atom_span_radius` unit tests (empty → null, molecule-in-vacuum ignores box, single atom → 0).
- `pnpm check` 0 errors; full vitest 4439 passed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d8a3717efb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.