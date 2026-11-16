# Issue

**Title:** Document that sci_solver receives sorted CI strings (backport #423)

## Description

First step toward #312: documenting the ordering guarantee is what lets a Fulqrum-side `sci_solver` factory rely on the loop's output. It does not address that issue's question of whether `sci_solver` should take the integrals at all.

`diagonalize_fermionic_hamiltonian` has always sorted the CI strings of each subspace before calling `sci_solver`, in the private `_apply_shape_constraints`, but the `sci_solver` contract never said so. A solver that maps a flat eigenvector back onto determinants depends on that order. The Fulqrum guide already relies on it: it reshapes the eigenvector against Fulqrum's own sorted basis, and is correct only because the strings arrive sorted.

This makes the ordering part of the documented interface, so a solver can rely on it, and adds tests that pin it.

The existing suite does notice when the sort is removed, but only as numerical drift — a `spin_square` mismatch in the third decimal place, and an energy-ordering assertion in the trim tests. That is indistinguishable from the seed sensitivity those tests already carry and document, so it would not survive review as a real signal.

Also documents the ordering as a precondition of `solve_sci` and `solve_sci_batch`, which take `ci_strings` directly. PySCF's `selected_ci` locates excitations by binary search. I measured a 12 mHa error on one small case (H4/STO-6G, four determinants per sector) from passing the same determinant set unsorted, cross-checked against a dense FCI reference restricted to the same subspace. The energy is variationally wrong with no error raised. I have not surveyed how that magnitude varies with system or subspace size.

<hr>
This pull request was drafted by Claude Opus 5 under my guidance.<hr>This is an automatic backport of pull request #423 done by [Mergify](https://mergify.com).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5de3d0b3ac8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.