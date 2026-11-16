# Issue

**Title:** feat(viewer): visualize per-atom magnetic moment vectors (+ OUTCAR magmom parsing)

## Description

## Summary

Visualize per-atom **magnetic moment vectors** in the 3D viewer, mirroring the existing force-vector path.

- `compute_magmom_data` reads `site.properties.magmom`: a **scalar** (collinear / ISPIN=2 → drawn along z, sign = spin up/down) or a **3-vector** `[mx,my,mz]` (non-collinear → true direction). Arrows are coloured **red = up / blue = down**.
- Rendered with the same `Arrow` component as forces; a **"Magnetic Moments"** controls toggle appears only when the structure carries magmom (`has_magmom` gate).
- New settings: `show_magmom_vectors` / `magmom_scale` / `magmom_up_color` / `magmom_down_color`. en/zh i18n in parity.
- **OUTCAR parsing**: `parse_outcar` now extracts per-atom moments from the last `magnetization (x)` (+ `(y)/(z)` for non-collinear) tables into `site.properties.magmom`, so opening a magnetic VASP OUTCAR surfaces the toggle + arrows with no extra setup.

## Verification
- Unit tests: `compute_magmom_data` (scalar / vector / zero-skip / colour-by-sign) + `parse_outcar` magmom (collinear + non-collinear).
- Live: loaded an Fe antiferromagnet (magmom ±3) — red spin-up + blue spin-down arrows render (confirmed the exact `#e0524a`/`#4a6fe0` cones in the scene).
- `pnpm check`: 0 errors.

## Notes
- Data source: OUTCAR (added) + pymatgen structures that already carry `site.properties.magmom`. vasprun.xml does not reliably carry per-atom moments, so it is intentionally not parsed for magmom.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6615337aea73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.