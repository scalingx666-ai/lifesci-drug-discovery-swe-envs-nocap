# Issue

**Title:** Tools for the computations regarding the Hessian and eff. Hessian

## Description

Added:

1. projection of the Hessian
2. mass weighting of the Hessian
3. possibility to compute several hessians with different levels of theory
4. computation of the effective hessian between two different states for MECPs which is based on this paper:     https://doi.org/10.1002/qua.25124. For this, the calculation type has to be set to type=-1
5. printouts of vibspectrum and g98.out files. Caution: The intensities are set arbitrarily
Imaginary frequencies are set negative

The printed Hessian is still the non-projected and non mass-weighted Hessian analogous to the xtb Hessian printout

Input example to compute an effective Hessian would be:
`
input = "struc.xyz"
runtype="numhess"
threads = 4

[calculation]
type = -1
eprint = true
elog="energies.log"

[[calculation.level]]
method = "xtb"
binary = "xtb"
uhf = 0
dir = 's0'

[[calculation.level]]
method = "xtb"
binary = "xtb"
uhf = 2
dir = 't1'
`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `961902a89dc3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.