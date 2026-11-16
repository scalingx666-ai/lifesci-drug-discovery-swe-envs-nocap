# Issue

**Title:** Refactor interpolate and atomic grid

## Description

Sorry for the large pull-request.  This pull-request removes interpolate.py and refactors atomic grid.  The derivative of the spherical harmonics was added, interpolation with its derivatives as well, conversion from spherical to Cartesian derivatives and interpolation of Laplacian is added. 

The following was added

- Removed Interpolate.py and moved some of its tests to utils
      - Generation of spherical harmonics is moved from atomgrid to utils.py (ee2fb04e1846b076cd20f820b7492fec88c93efe)
      - Some of the tests were moved over (2c06d749813bba3fc25ae5e702f450edf73a2736)

- Changes to AtomGrid
        - When r=0, the phi and theta are undefined and this code sets them equal to zero.  This is problematic when one wants to          integrate a function over angles that doesn't depend on r and so they get the incorrect integral (e.g. spherical harmonic l=0,m=0).  I fix this by changing the method `convert_cartesian_to_spherical` so that if it is converting the atomic grid, at r=0, it sets the (phi, theta) points to be the Angular grid with degree at r=0 and added tests to confirm this (f571bac7550a6f198680cc16110ae0bfdf44da7f). 
        - When the user provided `degrees` to AtomGrid, these are stored as an attribute.  This is problematic because angular/Lebedev grid doesn't support all degrees. This is fixed so that the actual degrees used at each radial point is returned (e272e9a6ea119ec925b7e6819859443a1dc1274a).
        - Moved the part that integrates spherical angles from "generating splines for radial component" to its own function `integrate_angular_coordinates` function (9fe57ae92b0c0b4d0b1db579041515eea023e251). This method is common for interpolation and doing spherical averaging.
        - Updated the fit method to use the  `integrate_angular_coordinates` function (f6a284b80979297c5d973848bf7b9860c5895358), added two tests: radial components of spherical harmonic is ones (rest zeros) and  radial components of function r^2 Y_l^m should just be r^2 (4a457445e09710ca94d30f50ec2ce54219664372). Renamed fit method to `radial_component_splines` (16008c87f38f2df07492848df3f1541ada973b0b).
        - The interpolate function only returns the derivative of the radial component wrt to r.  I fixed this by adding (first-only) derivative of the interpolated function wrt to Cartesian/Spherical and (higher orders) for radial component (6ddc1a78a91720397bc21fb5113f0a47d826a3d7) and added tests for them for both Cartesian and radial components (3cc6274b66b1481e124a306524b18e4c090c08b1).  The higher order derivatives for radial components are needed for the Laplacian.
        - Added the interpolation of the Laplacian of a function (82faa929d19ab8099acbb099e69a3f5dc168b2d3) and added two tests for them (spherical harmonic is eigenvector and the Laplacian of Hydrogen/exponential function) (f45d998ab20b5ec877a7b3feffbfcdd1ae00f72b). I had a hard time to get accurate results for these and have set the number of points used for interpolation higher or set the interpolation region smaller.
        - From our meeting, I changed rotate to be integer only (with zero meaning no rotation) and updated get_shell_grid so that it re-generates the grid instead (d01943d9c791820887143be5bfc52ceddf767747).
      
- Changes to Lebedev.py
      - The degree can be zero and so fixed a bug that wouldn't occur if it was (648862503c4fc4f89c30ed91e59249bc95b24185).
      - Added degree attribute to Lebedev grid (9328f16e2e3cff2db38409f72079412e6b49fddf).
- Changes to utils.py
       - Added the derivative of spherical harmonics (bfbff4fe759b324ebbf7655196edf9bdb1c5cb68) and tests (6f35018d1927caafb17db3dcc39774e7b4adb729).  Note that when phi is zero, then the cot(phi) is undefined and so I set it to zero.  I have no idea how the code works, got formulas from [wolframalpha](https://functions.wolfram.com/Polynomials/SphericalHarmonicY/20/ShowAll.html) and was brute-forcing for many hours until it matches finite-difference. This could be because the spherical harmonic used in this code scales by sqrt(2) and removes the Conway Phase.  I wrote comments expressing where I didn't understand why it worked.
       - Added the conversion from derivatives in spherical coordinates to Cartesian coordinates (4f2bdc5d653a0b4f36a0c8d78d5e4431bf1ac4bb). If the radius is zero, the derivative wrt to theta,phi are set to zero and if phi is zero, the derivative wrt to theta is set to zero.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afe9e77e9717`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.