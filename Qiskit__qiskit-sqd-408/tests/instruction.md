# Issue

**Title:** Document SCIState's amplitude sign convention (backport #395)

## Description

## Summary

`SCIState.rdm()` and `spin_square()` hand the amplitudes to PySCF, which assumes a determinant orders its creation operators with every alpha operator before every beta one. However, this has gone undocumented in this package. The `amplitudes` docstring was precise about *which* determinant each amplitude belongs to and silent about its sign, and the `sci_solver` contract — otherwise thorough, down to multi-process collective semantics — did not mention it either.

A solver that orders them differently gets wrong values from both methods with no error raised, while its energies, `rdm1`/`rdm2`, occupancies and any selection by amplitude magnitude stay correct. That is not hypothetical: SBD interleaves the spins orbital by orbital, and the Python wrapper saw `spin_square()` of 0.036 for an exact singlet with an energy rebuilt from `rdm()` 89 mHa off. Fixed downstream in  which is also where the reordering phase is derived.

## Documentation

- `SCIState.amplitudes` states the convention, since that is the attribute it governs.
- The `sci_solver` output contract points at it, for someone who reads the contract and never opens the dataclass.

## Why the existing tests miss it

There are three `spin_square()` checks in `test/test_fermion.py` that look like this validation. Each one expands `sci_state.amplitudes` into an FCI vector with `_sci_vec_to_fci_vec` — a plain scatter with no phase arithmetic — then compares PySCF's `spin_square` of that against `sci_state.spin_square()`. Both sides consume the amplitudes under the same assumed convention, so the test agrees with itself whichever convention is used. Applying the reordering phase to a random state moves both sides together, from 1.358 to 1.729.

They also only ever exercise the built-in `solve_sci`, whose amplitudes come from PySCF and are correct by construction. Nothing fed `SCIState` a vector from an independent source.

## Tests

`test_sci_state_follows_pyscf_sign_convention` compares against physics rather than recorded output:

- over a full determinant space the eigenvector is a spin eigenstate, so `spin_square()` must be exactly `S(S+1)`;
- the energy rebuilt from the RDMs must equal the eigenvalue the solver itself returned.

Neither reference is a stored number, so the same body suits any eigensolver — the second assertion compares a solver against itself. Cases are an H3 doublet and H4/H6 singlets.

Full spaces only. On a truncated subspace the eigenvector is not a spin eigenstate and `spin_square()` legitimately drifts (0.007 for H4, 0.004 for H6), so there is no exact value to assert.

`test_wrong_sign_convention_is_caught` builds the deliberately wrong-convention state and asserts both quantities fail, so the first test passes because the quantities are right rather than because they are insensitive. It also asserts the magnitudes are unchanged, which records why everything else missed this.

`tox -e py,lint,docs` passes: 60 tests, no lint findings, docs clean under `-W`.

## Follow-up

- Applying this test to the other eigensolvers is worth doing separately (I will likely leverage Coheriq to do this, in a follow-up).
- An elementwise comparison would be a stronger check and would work on truncated subspaces, but it needs a fixed reference vector for a programmatically built subspace — a golden value, with the usual tradeoff that it is opaque about provenance. Worth weighing on its own.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.
<hr>This is an automatic backport of pull request #395 done by [Mergify](https://mergify.com).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bbfa4e36e79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.