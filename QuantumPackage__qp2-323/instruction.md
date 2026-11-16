# Issue

**Title:** ORMAS implementation

## Description

This allows applying constraints to the determinants in the wavefunction using the [occupation-restricted multiple active space (ORMAS) method](https://doi.org/10.1063/1.1615954).
The multiple active spaces are specified by the first orbital index in each space: `bitmasks.ormas_mstart`, which is a 1d array of length `bitmasks.ormas_n_space`.

For example: in a system with 50 orbitals, if `bitmasks.ormas_mstart` is set to `(1,10,15,30)`, there will be four active spaces, with the first space consisting of orbitals `[1,2,...,9]` the second space `[10,11,...,14]`, the third space `[15,16,...,29]`, and the last space `[30,31,...,50]`.
If the first starting index is not set to `1`, then there will be no restriction on the orbitals with indices below the start of the first ORMAS active space.

The occupation restrictions are specified by two 1d arrays of length `bitmasks.ormas_n_space`: `bitmasks.ormas_{min,max}_e`, which are the minimum and maximum allowable number of electrons within the orbitals in that active space.

`ormas_bitmask` contains bitmasks corresponding to each space for easier checking to see if a determinant is allowed.
The subroutine `ormas_occ(key_in, occupancies)` will set `occupancies` (list of ints) to the number of electrons in each ORMAS space for the determinant `key_in`.  If each of these is between the allowable `ormas_{min,max}_e`, then the determinant is allowed.
The function `det_allowed_ormas(key_in)` returns `.T.` or `.F.` depending on whether the determinant is allowed (it will exit early with `.F.` as soon as it finds a space that does not obey the min/max elec constraints).

The actual filtering is performed during the selection in the same place as other similar restrictions (CAS, seniority, DDCI, etc.)

As it's currently written, this PR only allows ORMAS spaces which are contiguous; it should not be difficult to modify it so that each space is given as a list of orbitals (rather than just a starting index for a space that implicitly extends up to the MO preceding the start of the next space).

This implementation also only allows disjoint active spaces.  This could be changed, but it would complicate things like ORMAS-SCF or doing rotations to form natural orbitals where the user might not want to mix orbitals between different active spaces.  For cases where overlapping spaces would be necessary, it should be possible to specify an equivalent set of restrictions using disjoint spaces with a more complicated set of allowable electron counts in each space.  Another workaround would be to allow overlapping spaces, but when any orbital rotations are performed each intersection of spaces will be considered its own space (i.e. not allowed to mix with any of the overlapping sets that it is a part of).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `650101a2dede`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.