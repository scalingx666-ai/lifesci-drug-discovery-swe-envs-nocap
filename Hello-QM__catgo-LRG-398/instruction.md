# Issue

**Title:** feat(viewer): perceive + render bond orders (double/triple/aromatic) in the 3D viewer

## Description

Brings bond-order perception + rendering into the live 3D viewer. Conjugation is shown everywhere it exists — molecular adsorbates AND carbon-framework catalysts (graphene, C3N4, h-BN, COF). Inspired by AtomCanvas (MIT); the perception is a TS port of a lightweight RDKit-free valence heuristic (the right base for materials — RDKit/xyz2mol cannot run on metal/periodic/no-charge systems).

## What it does (gated by the default-OFF `Bond orders / 键级` toggle)
- **Perceives** double / triple / aromatic orders across the whole structure (every organic connected component). Metals stay single-bonded (no organic SP2 → no fake orders), so a Pt slab is unchanged.
- **Renders** doubles as offset twin cylinders, triples as three, and aromatic rings as a single solid **inscribed torus ring** per hexagon (textbook benzene circle) — ring bonds stay single sticks.
- **PBC-aware**: hexagons that close through cross-cell bonds are detected + deduped (one ring per distinct hexagon), and each ring centroid is wrapped back into the unit cell so boundary rings tile with the visible atoms (no floating rings).

## Correctness
- CO2 (O=C=O) → two clean C=O doubles (gated carboxylate-resonance so it is not mistaken for a carboxylate).
- Graphene/C3N4 → an aromatic ring in every hexagon; benzene → one ring; CO → triple.
- Reaches the ACTIVE instanced bond renderer (not a dead path).
- **Default OFF → byte-identical** (perception never runs, no overlay).
- 25 vitest (perception, ring detection, PBC dedup + wrap, CO2/CO/formate, metal-exclusion).

## Notes
- Opt-in: perception runs only when the toggle is ON, so large-system cost is user-controlled.
- Limitation: an adsorbate covalently fused into a carbon framework shares that component (conjugated into the sheet) — physisorbed and discrete molecules perceive normally.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `162740544ae8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.