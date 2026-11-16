# Issue

**Title:** implement generic inchitomol() with stereo support

## Description

This PR solves #137 and supports parsing of stereo information.

```julia
julia> mol1 = smilestomol("[D]O[D]")
{3, 2} simple molecular graph SMILESMolGraph

julia> i1 = inchi(mol1)
"InChI=1S/H2O/h1H2/i/hD2"

julia> inchitomol(i1)
{3, 2} simple molecular graph SDFMolGraph

julia> mol2 = smilestomol("C[C@H](O)C(=O)O")
{7, 6} simple molecular graph SMILESMolGraph

julia> i2 = inchi(mol2)
"InChI=1S/C3H6O3/c1-2(4)3(5)6/h2,4H,1H3,(H,5,6)/t2-/m0/s1"

julia> inchitomol(i2)
{7, 6} simple molecular graph SDFMolGraph

julia> inchitomol(i2, stereo = false)
{7, 6} simple molecular graph SDFMolGraph
```
<img width="342" height="212" alt="image" src="https://github.com/user-attachments/assets/a59e18fb-1227-4f4d-bb48-014e4a1d8c6a" />
<img width="328" height="267" alt="image" src="https://github.com/user-attachments/assets/b3bf6cbe-6ee7-43f5-b163-36926585cae3" />
<img width="339" height="278" alt="image" src="https://github.com/user-attachments/assets/ce34e6f8-a341-4963-b56c-88167a37d5f7" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c4498363381`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.