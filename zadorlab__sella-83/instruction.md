# Issue

**Title:** IRC: apply the first-step guard on ASE >= 3.28

## Description

.

On ASE >= 3.28, `Optimizer.irun` checks `gradient_converged()` rather than `converged()`. `IRC` only overrode `converged()` (where the `self.first` first-step guard from #78 lives), so the guard was bypassed: an IRC started from a TS with `|F| < fmax` "converged" before the first step, never applied the initial displacement, and returned 0 steps (forward == reverse == input TS).

This overrides `gradient_converged()` to route through `converged()`, so the first-step guard (and the `evals[0] > 0` check) still apply. Backward-compatible — older ASE that calls `converged()` is unaffected.

**Verified:** the minimal repro from #82 goes from `nsteps=0` to `nsteps>0`, with forward/reverse descending to the two opposite minima. Also confirmed on real transition states (an MLIP TS search): reactions that previously returned "No reaction" now give proper IRC endpoints. Adds `tests/test_irc.py` as a regression test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df7218ab7d1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.