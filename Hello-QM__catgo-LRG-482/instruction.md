# Issue

**Title:** feat(viewer): MatCap atom render style (ceramic / clay / glossy / pearl presets)

## Description

## Summary

Add a **MatCap** (material-capture) atom render style — a cheap, orbit-stable way to give atoms a real material feel via a single texture lookup instead of per-fragment lighting.

- New `render_style` value **MatCap**, plus a **MatCap preset** dropdown (shown only when Material = MatCap): **Ceramic / Clay / Glossy / Pearl**.
- Presets are generated **procedurally** (a grayscale lit sphere baked on a canvas, zero asset / offline-safe). The atom shader samples it by the view-space normal and multiplies by the per-element colour, so every atom keeps its element identity while gaining the matcap shading.
- Wired into the default `AtomManagerInstances` impostor shader (render-style int 3); the legacy `AtomImpostors` path falls back to glossy. en/zh i18n in parity.

## Verification
- `pnpm check`: 0 errors. Live: verified ceramic / glossy render cleanly (soft studio-lit spheres, element colours preserved).

## Notes
- A **Metallic** matcap was prototyped and **dropped**: a procedural grayscale sphere reads as plastic, and a real chrome photo (× element colour) either washed out or crushed atoms to black across colour-space attempts. Convincing metal needs true IBL/env-map on atoms (a separate, heavier change). The four kept presets all render well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6615337aea73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.