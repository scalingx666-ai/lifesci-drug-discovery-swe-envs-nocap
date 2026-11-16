# Issue

**Title:** Refactor documentation in onedgrid and rtransform

## Description

This pull-request refactors (mostly documentation fixes) for onedgrid.py and rtransform.py.  

Key changes are:
- Added type hinting
- Changed the documentation in both files by fixing typos, adding equations, some references.
- Made it more explicit as to which intervals it's being mapped to in the documentation.
- Fixed flake8 and black issues
- cfcffc214e528b22ef7331ad9b541572c9c9a875 For Trefethen transformation in onedgrid.py, I made it more explicit that the d parameter is the degree of the Taylor polynomial of sin^{-1} and changed it so that it matches the equations, i.e. d=1 is identity, d=3 is the third degree etc. See the paper in [dropbox](https://drive.google.com/drive/folders/1ZBL50iFLchFspMYMcaNon_5seCrWAYua).
- da8509e685df865a5a0e6a0383dc1a39c7b63f8e Changed the naming of TF to RTransform to make it consistent across all classes in rtransform.py
- I changed HortonLinear to UniformInteger, because this generates an equally-spaced integer grid from 0 to N-1 with weights equal to one.  This plays a huge role below.
- The problem in issue #125, is that the MultiExponential transform transform points to `f(x) = -R log ((x + 1) / 2)` and thus it swaps the endpoints `f(1) = 0` and `f(-1)=infty`.  Hence, when the base class OneDGrid transforms, it sees that the bounds [infity, 0] is invalid because it isn't ordered correctly.  I fixed this in 4b17f0a25bd5171c5baeaa27b0041a0d578f8f41 by always sorting the domain to get [0, infty].

The biggest issue I have is the radial transformations (LinearRTransform, ExpRTransform, PowerRTransform, HyperbolicRTransform) which were obtained from [Horton/grid.py]() and how the documentation in python grid isn't correct as to what the domain/codomain are and they seem to be very specific to HortonGrid/UniformInteger class.   For example, for LinearRTransform it transforms according to `r(x) = rmin + x*(rmax - rmin)/(npoint - 1)`, where npoint is the number of points, rmin is the minimum of grid and rmax is maximum of grid.    

The docs claim that it maps to `[r_min, r_{max}]` but this is only true if you're using HortonLinear/UniformInteger grid.  This is also a problem in ExpRTransform and PowerRTransform, where it only maps to `[r_{min}, r_{max}]` only if you're using HortonLinear grid.  One easy way of fixing this, is to replace `npoint - 1` to taking the maximum over all grid points i.e. `np.max(grid.points)`, this will hold true for any grid.

For HyperbolicRTransform, the mapping `r(x) = ax/ (1 - bx)` where a, b are positive scalars. It doesn't map to [0, \infty) but rather it can map everywhere.  Additionally, there is the constraint `b(npoints - 1) >= 1` that isn't explicit in the docs, I'm assuming it is also specific to HortonGrid where it centers the singularity at `npoints - 1` and you only want the positive points on the left-side of singularity, see [desmos/grapher](https://www.desmos.com/calculator/ik0eevj29b), where `N=npoints`.

References
----------------
List of radial transforms:  https://www.pamoc.it/tpc_num_int.html#VOL-B

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68f9bea1e6e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.