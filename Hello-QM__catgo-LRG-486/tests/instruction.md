# Issue

**Title:** feat(viewer): elegant atoms + polyhedra — fix double-sRGB, GGX glossy, soft palettes

## Description

## Summary

Make the 3D viewer render colours correctly and look more elegant — atoms, polyhedra, and a global colour-space fix.

### Colour-space bug (global — affected every structure)
The element/bond colour helper did `Color.set(hex).convertSRGBToLinear()`, but `Color.set(hex)` already converts sRGB→linear (three's `ColorManagement` is on by default), so **every colour was linearised twice** and rendered too dark. Mid-tones collapsed — Fe gold `#b57200` turned muddy brown (verified: `#b57200` double-linear = `(46,5,0)` = the on-GPU `instanceAtomColor`). Dropped the redundant convert (2 sites). Colours now render at their true brightness — this corrects **all** atom/bond colours, every render style.

### Glossy atoms → physically-based
Replaced the hand-rolled Blinn-Phong glossy (a big plastic highlight) with **Cook-Torrance GGX** (roughness 0.2 → a small, bright, centred hot spot) + Smith geometry + Schlick Fresnel + ÷π energy-conserving Lambert, lit by ambient + a near-head-on HDR key through ACES, plus a soft **rim shadow** (grazing-silhouette darkening) for volume.

### Palettes
Add hand-tabulated soft element tables (terracotta O `#e15949`, sage Li `#8cd37e`, ochre Fe `#b67822`). `Vesta Soft` + new **`Jmol Soft`** use the tables, not a derived desaturation. Default `color_scheme` is the soft palette.

### Polyhedra
- Edges → fat screen-space lines (`LineSegments2`), light-grey `#cfd6e2`, `alphaToCoverage` (uniform 1px, not jagged 1-device-pixel GL lines). New `polyhedra_edge_width` setting.
- Faces → smooth (radial) normals + Fresnel rim + frosted-white tint → glassy solids.

## Verification
- `pnpm check`: 0 errors.
- Live (pip `catgo app`, FeLiPO4): Fe renders gold, small centred highlights, muted palette + rim shadow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31995f5e96be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.