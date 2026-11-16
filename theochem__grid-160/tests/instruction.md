# Issue

**Title:** [added] alvarez covalent radii

## Description

Added the covalent radii database from:
    B. Cordero,.V. Gómez, A. E. Platero-Prats, M. Revés,J. Echeverría,
    E. Cremades, F Barragána, S. Alvarez, Dalton Trans., 2008, 2832-2838
    https://doi.org/10.1039/B801115J

Observations:
    - The C covalent radius value was taken as reported for Csp3
    - For Mn (Z=25), Fe (Z=26), and Co (Z=27) the covalent radii values were
      taken as reported for the low spin electronic configuration.
    - These covalent radii values can be accessed using get_cov_radii(atnums, type="alvarez")

    modified:   src/grid/utils.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1baeb4bfc604`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.