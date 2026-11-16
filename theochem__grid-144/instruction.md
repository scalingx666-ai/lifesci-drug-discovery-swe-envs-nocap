# Issue

**Title:** Refactor ode

## Description

This pull-requests refactors ode.py and makes a decent amount of changes.

Features
------------
- Remove the class structure and turn everything into functions (39372cb6d6e88bf2dd0d92fedd78410653df6d9a).
- Improve the documentation with formulas for all functions 
- Add the ability for the user to add their own initial guess and change the max_nodes in scipy.integrate.solve_bvp. This was to make sure the boundaries were satisfying the constraint for more accuracy.
- The code only supported transforming three order ODE, added the ability to transform higher orders (f5ceb2149a6a26cc057b8e621aef12ff664b9166)
- Changed it so that the solution to the ODE when using a transformation to a new coordinate is with respect to the old coordinate rather than the new coordinate.  This also converts higher-order derivatives as well.
- Added a boolean attribute `no_derivatives` to solve_ode if the user knows they don't want the derivatives when using an radial transformation (point above).   This was to improve efficiency as converting derivatives has to occur point-wise with a for-loop.
- Remove the class structure in tests and used pytest.mark.parameterize to try more complicated examples and to clean code (bc4b3db64f62b499620f3deef59e56de845b0206).
- To the tests, I also made sure the nth derivatives are all accurate rather than just the function values (1f3baea3a0e1023744481c07f267eaa90d2576ec).
- Added a warning in case the leading coefficient is zero (cdd9a3ab153113ae98a8cac7d1b5af52169e316b).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `627c37579280`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.