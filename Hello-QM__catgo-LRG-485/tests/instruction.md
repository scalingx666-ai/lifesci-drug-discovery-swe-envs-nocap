# Issue

**Title:** fix(viewer): trajectory OUTCAR magmom + magmom display controls + anti-aliased atom edges

## Description

## Summary

Three viewer fixes, split out of the CLI-packaging branch (all verified live on a real magnetic OUTCAR).

- **Trajectory OUTCAR magmom** — #481 added per-atom magmom only to the single-structure OUTCAR parser, but a relaxation OUTCAR (2+ ionic steps) loads as a *trajectory* via `parse_vasp_outcar`, which dropped it. Export `last_magnetization` and attach the final converged magnetization block to the trajectory's last (relaxed) frame.
- **Magnetic-moment display controls** — a "Magnetic Moments" settings section (mirrors the force-vector one): `magmom_scale` slider + spin-up/down colour pickers, shown when magmom is on. en/zh i18n.
- **Anti-aliased atom silhouettes** — the impostor ray-sphere used a hard `discard` at the edge, so MSAA couldn't smooth the jagged outline (discard gives no sub-pixel coverage). Fade an analytic 1px edge-coverage band on the radial distance (`clamp((r - length(offset)) / fwidth(d) + 0.5)`) and enable `alphaToCoverage` on the opaque material, so the canvas's 4× MSAA anti-aliases the silhouette. (An earlier d²-based band read as a white halo — fixed to the radial 1px form.)

## Verification
- `pnpm check`: 0 errors.
- Live: loaded a NiOOH bulk OUTCAR (ISPIN=2, MAGMOM = 1 -1 1 -1…) — red-up / blue-down arrows render the AFM Ni ordering (±1.022 µB); atom edges smooth with no halo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0649cc8149be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.