# Issue

**Title:** Exclude to-self bond in 3B-bond correction list b3list

## Description

In rare cases, the three-body bond correction `ebatm` includes "to-self" bonds, where only two of the three atoms are different atoms. Since the distance of an atom to itself is zero, the `ebatm` was NaN in such cases. The new if conditions exclude the "to-self" bonds. While the if conditions slow down this step, it is only called once in the initialization, which can be neglected compared to the frequent `gfnff_eg` calls in optimizations or MD simulations.

Eventually, this could be achieved by adjusting the loops here or nbondmat_pbc https://github.com/grimme-lab/xtb/blob/efe263fdc96779d76590fd5bcf33254c9cbcaa68/src/gfnff/gfnff_ini2.f90#L1939
However, this would require very elaborate testing of the periodic version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dabf3071c0cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.