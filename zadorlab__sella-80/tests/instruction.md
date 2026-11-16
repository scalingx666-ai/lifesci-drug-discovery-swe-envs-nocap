# Issue

**Title:** Internal coord fixes

## Description

The recent aiopt test set applied to Sella revealed a number of small bugs that needed addressing. This PR resolves those bugs. Generally, they involved:
1) rotations becoming degenerate and the autodiff blowing up. I replaced it with a hand-derived closed form for the Hessian through an eigendecomp that doesn't rely on autodiff and thus avoids singularity (or rather, it handles the singularity more gracefully without diverging)
2) along with those degenerate rotations, the identity of the basis vectors in the 2D space spanned by these degenerate rotations was not well defined, causing essentially random changing of the basis vectors. These were stabilized into a "maximum-overlap" style so that the BFGS Hessian at each step is looking at a maximally consistent set of basis vectors.
3) There were some errors in how dummy atoms were being added for linear bends. First, adding multiple dummy atoms for linear fragments didn't invalidate the position cache between additions, leaving the second fragment with a degenerate rotation eigenspace. Second, for linear molecules like CO₂, both dummy angles were constrained (they're supplementary), preventing the optimizer from bending the molecule

Minor and not a bug: I expanded the trust radius recovery slightly for minimizations only (TS opts keep the same tighter recovery window). The growth window [0.966, 1.035] -> [0.75, 1.333] for order=0. I also made slightly more informed guesses for translation and rotation coordinate guess Hessian diagonal. 70 eV for a translation was way too stiff.

  ## Test plan

  - [x] All existing tests pass
  - [x] Benchmarked against 1752-molecule GFN2-xTB test set — fixes 7 of 8 previously-failing fragmented molecules
  - [x] No regressions in non-fragmented molecule convergence

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e4626c96262`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.