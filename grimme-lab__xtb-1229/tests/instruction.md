# Issue

**Title:** Fix Fukui function for PTB and change spin-state assignment

## Description

### Modified unpaired electron assignment
- The previous spin state assignment set the wavefunction to be open-shell for the anionic case if the original wavefunction has already been open-shell (see the relevant line of code below). If I don't have a major logic issue this seems to have been wrong in general before (`wf_an` is only a copy from the ground-state wavefunction calculated before), and the other way round would be correct (in the simplest case: a neutral closed-shell molecule becomes open-shell in the ionized case). The spin state assignment has been changed to a more reasonable logic.
```Fortran
if (mod(wf_an%wfn%nel,2).ne.0) wf_an%wfn%nopen = 1
```

- Since PTB does not allow for restarting a calculation, assigning the spin state only in the wavefunction does not have any effect. Before, the Fukui calculation crashed since `mol.uhf` didn't match the changed charge anymore (number of electrons was odd in a closed-shell calculation). Here, `mol.uhf` is changed accordingly (in the simplest case; from closed-shell to `mol.uhf=1`).
- Caution: The Fukui results for GFNn-xTB might also change since the `nopen` assignment has been changed.

### Additional changes
- enable PTB parameter loading for Fukui calculations as well
- minor formatting adjustments

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc10da86ee73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.