# Issue

**Title:** Multipole Moments and Recursive Spherical Harmonics

## Description

This pull-request implements calculation of spherical harmonics recursively, and implements the different multipole moments.

Details
---------
- Rename the previous spherical harmonic function to include the term scipy, and changed the order so that it is in Horton 2 order e.g. (l, m) = (0, 0), (1, 0), (1, 1), (1, -1) 
- Implemented recursive spherical harmonic function evaluation (in spherical coordinates).  This was done using forward recursion from the paper listed in the docs.  There is two sets of recursions, one that can handle degrees > 1900 using double precision and one that cannot.  I implemented the latter, and wrote in the note section in the docs regarding this problem.  To get around this, I used `np.longdouble`  which would use higher precision for 64 bit machines and avoid this problem but for 64 bit machines.
- Also implemented the solid harmonics and tested it against analytic examples.

- In the basegrid class, I've added a moments function with signature `def moments(self, orders: int, centers: np.ndarray,  func_vals: np.ndarray, type_mom: str = "cartesian", return_orders: bool = False,)`.  Provided an option to return which row corresponds to which order, e.g.` (n, l, m) =(1, 2, 3) or (l, m) = (0, 0)`.  The options for `type_mom` are `cartesian`, `radial`, `pure` and `pure-radial`.    The formulas are written in the function docs.
- The tests for moments are added in AtomGrid which are:
    -  Cartesian moment integral were tested with Gaussian upto order=1 against Wolframalpha
    -  Pure moment integral were tested against identity function and make sure it is all zeros past the first solid harmonic.
    -  Pure moment integral were tested of a Gaussian against Horton.
    - Radial moments were tested against Horton
    - Pure-Radial moments were tested on identity function to make sure it is similar to doing a pure and tested against spherical harmonics.
    
- Added to tox.ini for flake8 to avoid the error when using lambda functions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1baeb4bfc604`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.