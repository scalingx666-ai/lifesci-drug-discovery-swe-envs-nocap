# Issue

**Title:** Keep separate molecules apart in Spin 3D

## Description

## Summary
One drawn object can hold several disconnected molecules (for example `c1ccccc1.CC(C)(C)C.OCCO`). Both 3D engines return each fragment's conformer centred on the same origin, so Spin 3D piled them at the centre and they stayed piled while rotating (confirmed on macOS and Windows).

- `interaction/spinFragmentPlacement.ts` puts each fragment's 3D centre at its 2D centre in the opening view frame and spreads crowded fragments just enough that they never overlap.
- The arrangement is stored in page units when Spin opens and reused for the refined conformer, so fragments stay still at the hot-swap; the scale is recomputed as before.
- The overlap correction is capped (fragments²) with a guaranteed spread-out fallback.
- RDKit and the OCL fallback share the path; release/flatten and reopen keep the fragments apart; chemistry is unchanged (canonical SMILES, atoms, bonds, charges, stereo).
- A single molecule is handled exactly as on main.

## Tests
- New: `spinFragmentPlacement.test.ts`, plus `spin3dSession.test.ts` cases for RDKit and OCL (overlay → flatten → reopen), a single-fragment exact-match case, and differing embedded/refined extents. Verified they fail on the two earlier commits of this branch.
- AGENTS.md §9 suites (spin3dModel, spinFlatten, spinFlattenStereo, flattenRoundTrip, interaction): 176/176. Lint OK. The local full vitest ran under load average 185, and its 128 failures were in one DOM file that passes 148/148 alone; CI is the full check.
- `docs/manual-stress-checklist.md`: new Spin 3D multi-molecule line.

## Platforms
- macOS: automated tests only; hands-on pending (new checklist line + single-molecule regression).
- Windows: CI; hands-on pending (same items).

Reviewed by Kimi K3 and Claude Opus (three passes; all findings fixed).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `949ac0b6dbb1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.