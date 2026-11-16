# Issue

**Title:** viewer polish: atom_radii bond default, glossy/metallic lighting, brighter seam-free bonds

## Description

Four viewer default/appearance tweaks (all live-verified on TiO₂ / Si).

### 1. `chore(bonds)` — default bonding strategy = atom_radii everywhere
The viewer setting default was already `atom_radii`; align the rest so nothing falls back to `electroneg_ratio`: VS Code ext default + enum order, and the viewer strategy fallbacks.

### 2. `chore(viewer)` — glossy key light → azimuth 0 / elevation 5
Head-on key (was az17/el11) for a more centred specular hot spot.

### 3. `feat(viewer)` — metallic gets a bigger, softer highlight (pretty-lattice port)
Metallic shared glossy's hardcoded GGX roughness 0.2. Add per-render-style `uRoughness`/`uMetalness` (metallic 0.4/0.4) — a wider, element-colour-tinted highlight — plus the matching bright near-head-on key (2.5) / high ambient (1.0). **Glossy is byte-identical** (metalness 0, roughness 0.2 → same math).

### 4. `fix(viewer)` — brighter bonds, no dark seam down the cylinder
`BondManagerInstances` (default instanced bonds) rendered cylinders ~0.4× their base colour (too dark) and had a **dark line down each bond** — its studio env summed a key + near-opposite fill lobe, leaving a dark valley on the strip perpendicular to both. Replaced with a flat ambient floor + single soft key so bonds match their end atoms with a gentle highlight and no seam. (DashedBond/Bond.svelte use a different, profile-driven path — unaffected.)

## Verification
- `pnpm check` 0 errors; targeted vitest green (bonding/coordination/settings/scene).
- Live screenshots: bonds no longer dark / seamed; metallic highlight visibly bigger than glossy; glossy pixel-identical before/after the shader refactor.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e2893f71cbe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.