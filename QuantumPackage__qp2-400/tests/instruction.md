# Issue

**Title:** davidson: report the right S^2 for the fill states

## Description

## Problem

In `src/davidson/diagonalize_ci.irp.f`, the Lapack branch with
`only_expected_s2 = true` first stores the `i_state` eigenvectors whose S^2
matches `expected_s2`, then fills the remaining slots up to `n_states_diag`
with the other eigenvectors. The fill loop copies eigenvector `j` into slot
`i_state+i_other_state`, but reads the S^2 at the *slot* index:

```fortran
CI_eigenvectors(i,i_state+i_other_state) = eigenvectors(i,j)
CI_electronic_energy(i_state+i_other_state) = eigenvalues(j)
CI_s2(i_state+i_other_state) = s2_eigvalues(i_state+i_other_state)  ! wrong index
```

A fill state can therefore print the S^2 of an unrelated eigenvector, possibly
one belonging to another spin multiplet.

## Fix

Read the S^2 of the eigenvector that is actually copied (one line):

```fortran
CI_s2(i_state+i_other_state) = s2_eigvalues(j)
```

The energies and the eigenvectors are untouched; only the S^2 reported for the
fill states changes.

## Reproduction

H2/STO-3G CISD with `n_states = n_states_diag = 4` and the Lapack
diagonalization (`diag_algorithm = Lapack`, `only_expected_s2 = true`,
`expected_s2 = 0`). The diagonalization returns the printed states in the
order singlet, triplet, singlet, singlet: the triplet sits at eigenvalue index
2 while `s2_eigvalues(4)` holds the S^2 of the highest singlet. `i_state = 3`,
so the triplet is copied into slot 4.

`h2.xyz`:

```
2
H2
H 0.0 0.0 0.0
H 0.0 0.0 0.74
```

Commands:

```
qp_create_ezfio -b sto-3g h2.xyz -o h2.ezfio
qp_run scf h2.ezfio
printf '%20d\n' 4 > h2.ezfio/determinants/n_states
printf '%20d\n' 4 > h2.ezfio/davidson_keywords/n_states_diag
qp_run cisd h2.ezfio
```

Before the fix, the last state block printed by `qp_run cisd` is:

```
* Energy of state    1                              -1.137283834649179
* S^2 of state    1                                  0.000000000000000
* Energy of state    2                             -0.1683524420384719
* S^2 of state    2                                  0.000000000000000
* Energy of state    3                              0.4831426566244119
* S^2 of state    3                                  0.000000000000000
* Energy of state    4                             -0.5307733648088220
* S^2 of state    4                                  0.000000000000000
```

State 4 is the triplet, reported with the singlet S^2 of the fourth
eigenvalue. After the fix, the last line becomes:

```
* S^2 of state    4                                  2.000000000000000
```

All four energies are identical before and after the change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca833a6a3d32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.