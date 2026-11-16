# Issue

**Title:** feat(viewer): render_style material mode (Glossy/Matte/Toon) + per-style lighting controls

## Description

Adds a publication-style **material mode** to the live 3D viewer plus a full per-material lighting control group. Inspired by AtomCanvas (MIT); implemented natively in CatGo's Svelte/Three.js stack.

## Material mode (render_style)
New `render_style` setting — **Glossy / Matte / Toon** (中文: 光泽/哑光/卡通) — orthogonal to color_scheme (palette). Applies to the active instanced/impostor atom renderers + bonds.
- **Glossy** — specular Blinn-Phong (default look)
- **Matte** — diffuse, no specular
- **Toon** — 3-band cel shader (ported from AtomCanvas ToonHighlightMaterial), preserves the silhouette outline

## Lighting controls (new "Lighting" group)
- **Direction**: azimuth + elevation sliders → view-space headlamp, live.
- **Brightness**: directional + ambient intensity, and highlight (specular) strength — all live, no shader recompile.
- Fixes the shared headlamp, which was lit from lower-left (exposed by toon's hard bands) → now upper-right / from above.

## Per-style lighting profiles
The 5 lighting params are **per render_style**: glossy/matte/toon each carry their own profile (matte/toon default highlight 0). Switching material swaps the active profile; **edits are remembered per material**; reset restores only the active style. Persisted in viewer settings (localStorage, debounced).

## Notes
- Glossy is the default; existing structures render unchanged except the agreed headlamp-direction fix.
- Toon is self-lit, so its ambient/directional/highlight sliders are inert (kept for slider consistency).
- Type-check clean (no new errors); settings vitest green.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `314abf5b9d22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.