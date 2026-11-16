# Issue

**Title:** Cubic/Uniform grid class

## Description

This pull-request is regarding Grids in three dimensions.   There are three classes: _CubicGrid, Tensor1DGrids, and UniformCubicGrid.   Here, I define cubic to be that it is specified by 3 indices (i, j, k) (which I think is usually defined as a cube),  and uniform means consequent points are evenly spaced.   This implies that a parallelepiped is cubic, even though  it is slanted cube.

Tensor1DGrids and UniformCubicGrids are children of the base class _CubicGrid.  This base class contains the interpolation function, which utilizes Cubic interpolate with scipy.   

UniformCubicGrids class is largely copied from [chemtools.utils.grid](https://github.com/theochem/chemtools/blob/master/chemtools/utils/cube.py).  UniformCubicGrids contains four integration weighting scheme from the file [cubicintegrations](https://drive.google.com/file/d/18apJ_2vzZH71kE1pW3CDcIRhG53JyMn5/view?usp=sharing). These weighting schemes are tested with a simple Gaussian (TestUniformCubicGrid.test_integration_with_gaussian) inside test_cubic, and unfortunately, I was only able to achieve two decimal place precision.  The calculation of the integration weighting scheme were vectorized, and the tests compare them to the brute-force method.

Inside chemtools.utils.cube (UniformCubicGrid._calculate_volume), the volume is calculated assuming if the rows in the "axes" attribute are orthogonal to one another, else the volume should be computed like a [parallelepiped](https://mathinsight.org/image/volume_parallelepiped).  I'll need someone else to confirm this.  This assumption of orthogonal axes isn't stated in the docs in chemtools either.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4667f43eb44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.