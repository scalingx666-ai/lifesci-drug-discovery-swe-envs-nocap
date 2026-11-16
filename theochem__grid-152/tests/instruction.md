# Issue

**Title:** Refactor poisson.py and ode.py

## Description

This pull-requests makes changes to poisson.py and adds solving ode as initial value problem for ode.py

ode module
----------------
- Added solving ordinary differential equation as a initial value problem, called solve_ode_ivp (64eac5920f1114de31b42b8257545a10099132b8). I renamed the previous ode method to solve_ode_bvp, since it solves it as a boundary value problem.  The function that takes the solution of these ode and reconstructs the function is added a seperate function (4d614f5f41a32411df2c8e03da3cb63d904af042) since it is used by both solve_ode_ivp and solve_ode_bvp.
- Two tests were added to solve_ode_ivp  (7fedcdd921f6f465f3be103dd76307795babab18):
    - Compared it against analytic examples (without using radial transformation). These analytic examples were solved using woflramalpha.
    - Compared the solution using transformation and without transformation and made sure the results matched each other. The transformation were chosen so that the minimal point `r_{min}` matches the initial point of `x_span`.

Poisson module
---------------------
- Removed the previous Poisson module and added solving poisson as bvp or ivp problem (765ac44a076ce0850f0e621a136ee070de3bc8b9).
     - For `solve_poisson_bvp` function, it has the option of including the `r=0` point and removing large points (useful when radial transformation gives infinite values or 1e6 values).  This greatly helped in increasing accuracy.   The boundary value problem is optional, and if not provided it computes the boundaries instead.
     - For `solve_poisson_ivp` function, the initial value problem is calculated based on the following asymptotic to the solution of the Poisson:
![image](https://user-images.githubusercontent.com/10901502/180804086-1186e781-5e62-446b-b671-f745cda118e4.png)
The derivative of this gives the initial value for the derivative for large x.
- The following tests were added for Poisson (1d86225e63957706f1f094343614b85a1ccb4cd2)
     - Tested with analytic result for `solve_poisson_bvp` with unit-charge distribution (f(x) is Gaussian) whose solution is error function `erf(r)/r` that is undefined at `r=0`. 
     - Tested the solution from `solve_poisson_bvp` with interpolate_Laplacian, unfotunately the Laplacian  isn't accurate with `r\approx 0` and so it was only tested on region `r\in)** Fix a bug in finding the radial components inside atomic grid (06d45772a1da6ba75377a54078636d55fed825c2).  General function  expanded in the real spherical harmonic basis:
![image](https://user-images.githubusercontent.com/10901502/180798946-459632f5-e8b5-42ee-be06-de5257a73b86.png) where ![image](https://user-images.githubusercontent.com/10901502/180799152-f4f35acd-e04b-4bef-961b-50c796983b3b.png) but this integral is calculated as a Lebedev grid that can only integrate spherical harmonics up to `l_max`. Since multiplication of two spherical harmonics adds their degree, it can only integrate up to `l_max //2`, anything above that is inacurrate and thus set to zero.
- For some radial transformation that can give infinite values, the `trim_inf` attribute wasn't correctly applied and it wasn't added to the first derivatives. This is fixed in (5b5fd47ab487b789ab8bdee38dc6a65264a3be35)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3edfb576ef44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.