# Issue

**Title:** feat(structure): polyhedra bond-graph rewrite, distance-rule bonding, live polyhedra controls

## Description

Reworks coordination polyhedra onto a bond-graph algorithm (matterviz-aligned) and overhauls per-element-pair bond distance rules, plus several viewer fixes. Branched off main and re-merged latest `origin/main` (#357 unified pane-tree) — clean merge, 0 type errors.

## What's in here

**Polyhedra (bond-graph rewrite)**
- Replace the legacy distance-search polyhedra with a bond-graph algorithm: per-vertex anion classification, distance-factor trim, CN gate, framework/spectator filtering.
- Compute coordination-complete `atom_radii` bonds independent of the render bond mode (`solid_angle` under-coordinates octahedra).
- Image-atom polyhedra: copy a center's polyhedron to rendered boundary image atoms.

**Fixes**
- `fix(polyhedra): repaint live on opacity/edge changes` — threlte 8 renders on-demand and only auto-invalidates on `<T>` prop changes; the opacity/edge `$effect`s mutate shader uniforms in place, so changes didn't paint until a pointer event. Now `invalidate()` after each mutation.
- `fix(polyhedra): compute on unit-cell sites, not image-expanded` — with image atoms shown, `structure.sites` is expanded with boundary copies; feeding those to the bond graph double-counted each vertex (e.g. BaTiO3 Ti → CN 12 = 6 positions doubled), degenerating the convex hull into a half-shell. Slice to original sites; image-atom polyhedra are added separately.

**Features**
- `feat(polyhedra): per-element Centers picker` — element toggle chips choose which elements get polyhedra (empty = auto). `center_elements` is now a filter-only allow-list: restricts centers + skips the framework auto-hide, but keeps anion-vertex selection + distance trim (clean shells).
- `feat(bonds): bond distance rules add AND remove bonds, drive polyhedra` — a per-pair rule now fully defines that pair's bonds: every PBC pair within `[min,max]` becomes a bond (generate) and out-of-range bonds are dropped (filter). Applied to both the rendered bond graph and the polyhedra bond graph. Previously rules were post-filter only (couldn't add a missed bond, and polyhedra ignored them).
- `change(bonds): default bonding strategy → atom_radii` (coordination-complete, PBC-aware).

## Verification
- `pnpm check`: **0 errors** (302 pre-existing warnings).
- `pnpm test`: **4130 passing**; only the known-flaky `RdfPlot` test times out under full-suite load and passes in isolation (21/21).
- New unit tests: `bond-distance-rules.test.ts` (filter / generate / PBC jimage / dedup), polyhedra PBC + framework-filter + explicit-mode tests.
- Live-tested in the running app on BaTiO3 (full octahedron, live opacity) and LiFePO4 (Centers picker; Fe-O rule max 1.5 → Fe isolated + FeO6 removed; max 3.5 → extra long Fe-O bonds atom_radii never makes).

## Known limitation
- The large-system GPU bond path stays filter-only (does not generate rule bonds); the CPU/viewer path is the one that gained generation.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae2f24ecc3fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.