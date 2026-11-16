# Issue

**Title:** Dipole Moment Center of Mass Fix #188

## Description

Related to issue #188. I've added the isotopic masses of the most common isotope obtained from [here](https://www.chem.ualberta.ca/~massspec/atomic_mass_abund.pdf).    These are put in a dictionary inside `utils.py`. The jupyter notebook is then updated to use formaldehyde instead of water instead. Sorry, it seems that I was either lazy or forgot about it when I wrote the jupyter notebook.

The center of mass formula is obtained from [Wikipedia](https://en.wikipedia.org/wiki/Center_of_mass#A_system_of_particles).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fa074dd54ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.