# Issue

**Title:** fix projected frequencies

## Description

##  

Modifies the calculation of projected frequencies to not depend on the molecular orientation. 

This dependance arose because the previous implementation blindly followed the reference approach in which the projection is meant to create a block hessian matrix with structure
```
(0  0)
(0  H')
```
then discarding the first 5/6 rows that should be translations/rotations. However, if the rows were not ~0 then, depending on the chosen rotation vectors (which are coordinate dependent) https://github.com/duartegroup/autodE/blob/6a6eebe2b3c77c7a3f850b9e3c5cce32fafa7531/autode/hessians.py#L177-L179
then sometimes a vibrational mode could be discarded, leading to the wrong projected frequencies.

This PR
- Removes the random orientation of translational vectors as I don't think they're needed
- Checks the structure of the projected hessian before diagonalising a submatrix that has all the non-zero components
- Zeros not-quite zero modes that should be rotations (numerical issues?)

While debugging this I found that ORCA and Gaussian do something unexpected (to me at least). Their transform to normal modes is not a projection (i.e. eigenvalue preserving). For a distorted methane molecule
<img width="800" alt="ch4_distorted" src="https://github.com/user-attachments/assets/49c41e85-2908-46cf-84aa-0eb93aa07cbb">
you go from 2 strong imaginary frequencies unprojected (`Frequency(-881.98419 cm^-1), Frequency(-197.01737 cm^-1)`), to only one (`-178.5054 cm-1`). Plotting the energy along this mode 
<img width="350" alt="plot" src="https://github.com/user-attachments/assets/8a3f4766-de17-419e-a2db-bd8516416ded">
it's very much not a TS, so I am confused about what they're doing, and if it's ok

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ccbcc2b7446a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.