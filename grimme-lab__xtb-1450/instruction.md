# Issue

**Title:** Occupy every neighbor in get_bonds so all-torsions is atom-order invariant

## Description

`all torsions=true` applies a different set of dihedral constraints when the same geometry is written with a different atom order. On the public n-butane pair, the heavy-first xyz receives zero torsion constraints; the reversed xyz receives twelve.

`constrain_all_torsions` only walks atoms whose diagonal coordination `bond(i,i)` is at least 2. That number is written by `get_bonds` as the count of neighbors found in `do j = 1, i-1`. Carbon atoms that appear before their bonded partners therefore get CN 0 or 1, the torsion walk never starts, and the optimizer is unconstrained. The off-diagonal bond matrix is already symmetric; only the diagonal count is index-ordered.

This counts every neighbor in that inner loop (`j = 1, n`, skip `i`). Coordination is then the full neighbor count, independent of xyz permutation. The covalent-radius and scale-up logic is unchanged. Skipping hydrogens, or relaxing only the torsion gate, would not keep that identity.

.

Measured on the issue butane geometries with Pyykkö–Atsumi 2009 radii: heavy-first carbon CN was `[0,1,1,1]` (zero carbons with CN≥2); after this change it is `[4,4,4,4]`. Reversed geometry was already `[3,3,3,4]`; after this change carbon CN is identical under atom reversal.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa035bce99a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.