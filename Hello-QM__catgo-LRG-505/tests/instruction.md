# Issue

**Title:** feat(viewer): widen bond-thickness range + scale lattice axis arrows with cell line width

## Description

Ported from pretty-lattice's "adjustable structure line widths". CatGo already had `bond_thickness` (bond cylinder radius) and `cell_edge_width` (cell line width) as user sliders that feed exported figures automatically, so this is a small **gap-fill**, not a new control system.

## Changes
- **Widen the bond-thickness slider** to the config bounds: min 0.05→**0.01**, max 0.5→**1.0**, step 0.05→**0.01**, now read from `SETTINGS_CONFIG.structure.bond_thickness` (matches the cell_edge_width / bond_scale sliders' config-driven pattern).
- **Lattice a/b/c axis arrows now respect `cell_edge_width`**: their shaft (0.05) and cone-tip (0.175) radii scale by `cell_edge_width / 1.5`, so the width control affects the axis arrows too. Scale === 1 at the default 1.5 → today's look reproduced exactly; arrow proportions (length, cone height) unchanged.

`pnpm check` clean (0 errors). No new setting, no i18n change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de6275dceaf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.