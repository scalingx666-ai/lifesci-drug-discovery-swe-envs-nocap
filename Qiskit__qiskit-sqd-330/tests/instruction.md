# Issue

**Title:** Refactor diagonalize_fermionic_hamiltonian loop body into helper functions

## Description

## Summary

Splits the two large regions of the configuration recovery loop in `diagonalize_fermionic_hamiltonian` into helper functions:

- `_prepare_ci_strings` — configuration recovery / postselection, subsampling, and CI-string construction (returns the batch of `ci_strings`).
- `_process_results` — best-result update, convergence check, and carryover-string computation, returning a bundled `_IterationState`.

The loop body is now a flat, one-level-deep sequence: prepare → solve → callback → process. The mid-loop convergence `break` becomes a `converged` flag on the returned state.

## Why

This is a pure, behavior-preserving refactor that establishes cleaner seams in the loop. It is groundwork for the SPMD/MPI work in #329: with these helpers in place, the distributed version reduces to wrapping the two helper calls in a control-process check and broadcasting the single `_IterationState`, rather than deeply nesting the whole loop body and broadcasting several separate variables.

## Verification

- `tox -e lint` passes (mypy clean).
- `tox -e py` passes (21 tests).
- The extracted code was moved verbatim; a line-for-line comparison against the previous loop body shows the only differences are the `break` becoming a `converged` flag and the `sci_solver`/`callback` calls remaining inline in the main function.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74acd9e3e2b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.