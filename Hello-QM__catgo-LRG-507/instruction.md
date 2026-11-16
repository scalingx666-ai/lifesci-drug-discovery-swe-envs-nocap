# Issue

**Title:** feat(viewer): defer bond/polyhedra computation for very large (>8000-atom) structures

## Description

Ported from pretty-lattice. Very large structures compute bonds eagerly on load today (show_bonds defaults to `always`), which janks the viewer for 10k+ atom systems (e.g. LAMMPS kerogen). This defers bond+polyhedra computation for huge structures: atoms + unit cell render immediately, and a banner offers to compute bonds on demand.

## Design (conservative)
- `DEFER_BONDS_ABOVE_ATOMS = 8000` (strictly `>`) — well above the 1000 sync / 2000 GPU thresholds. **Below 8000 canonical atoms, behavior is byte-identical to today.**
- Gate = a `skip_compute` param on `compute_bond_connectivity` that reuses the existing `never`-branch clear (clears bonds, bumps generation, kills in-flight workers). Passed into the bond `$effect.pre`, the ferrox-ready recompute, and the polyhedra path.
- Count is the **canonical** atom count (`num_original_sites`), not the PBC-image-expanded scene count — so a small structure whose boundary images push the scene over 8000 isn't falsely deferred, and the banner shows the real number.
- Re-defers on each new structure load (keyed off atom count, not object identity, so in-place edits don't re-hide user-requested bonds).
- UI: a small "Bonds hidden for performance (N atoms) · Compute bonds" banner; clicking un-defers via the normal reactive path. Gated on `show_bonds !== 'never'`. i18n en+zh.

## Verification (live, CDP)
Loaded a 10976-atom Cu FCC supercell: atoms + cell rendered immediately, banner showed **"Bonds hidden for performance (10976 atoms)"** (canonical count, after the count fix), clicking **Compute bonds** removed the banner and rendered the full bond network. `pnpm check` 0 errors; 5/5 unit tests for `should_defer_bonds`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de6275dceaf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.