# Issue

**Title:** Hessian accuracy handling

## Description

Restore the historical optimization-level SCC accuracy settings and make Hessian accuracy handling consistent.

- Optimization levels again use the original SCC accuracy table.
- Explicit `--acc` overrides level-dependent and dynamic accuracy adjustments.
- Numerical Hessians default to tight accuracy (`0.2`).
- `--ohess`/`--bhess` use `0.2` for the Hessian, or the optimization accuracy if tighter.
- Simplify accuracy-state handling via `set%acc_set`.
- Update help/man pages accordingly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7817cb71563`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.