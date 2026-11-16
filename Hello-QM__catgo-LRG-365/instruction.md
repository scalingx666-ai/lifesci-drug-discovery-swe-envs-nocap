# Issue

**Title:** fix(bonds): correct all four bonding strategies + tunable scales + trajectory rule tracking

## Description

Fixes all four bonding strategies (live path = ferrox-wasm Rust) plus two UX/correctness gaps. Each commit is an independent, TDD'd fix; verified on the live wasm artifact (LiFePO4 / HCP / NaCl) and 11/11 cargo + 1209 structure vitest.

## Strategies
- **atom_radii**: absolute `Σr+0.3` window was too tight for metals → multiplicative `dist ≤ scale·Σr` (default 1.2), plus a user **Bond scale** slider (default 1.15).
- **electroneg**: (1) applied the missing matterviz closest-neighbour penalty — killed the 2nd/3rd-shell "hedgehog" over-bonding; (2) dropped the `ΔEN > 1.7 → reject` gate that silently discarded every ionic bond (Li-O, Na-Cl).
- **solid_angle**: replaced the radius-weighted sphere-cap (under-coordinated octahedra) with a real Voronoi tessellation via a non-periodic supercell — correct for ANY lattice (orthogonal + hexagonal/triclinic), exact jimage, deterministic jitter to avoid meshless_voronoi degeneracy panics; plus a covalent-radii distance sanity to trim anion-anion (O-O) polyhedra edges.

LiFePO4 now resolves to exactly Fe-O 24 / Li-O 24 / P-O 16, zero spurious; HCP 12-coordinate; NaCl 6-fold Na-Cl.

## UX / correctness
- Separate **polyhedra Bond scale** (polyhedra are built from a dedicated atom_radii pass).
- **Bond distance rules now track the trajectory frame** — ruled pairs were frozen at frame 0 while atoms animated; rules now use the current-frame positions.

Note: meshless_voronoi (already a dep) compiles AND runs under wasm; the `#[cfg(not(wasm32))]` gate in coordination.rs was conservative.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a14806408d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.