# Issue

**Title:** Woraround for brittle SVD on AMD GPUs

## Description

When running on AMD GPUs, we often get an error of the type:

```
ERROR: LoadError: ArgumentError: invalid argument #4 to LAPACK call
Stacktrace:
  [1] chklapackerror
    @ /capstor/scratch/cscs/abussy/dftk_beverin/julia-1.10.10/share/julia/stdlib/v1.10/LinearAlgebra/src/lapack.jl:38 [inlined]
  [2] gesdd!(job::Char, A::ROCArray{Float64, 2, AMDGPU.Runtime.Mem.HIPBuffer})
    @ LinearAlgebra.LAPACK /capstor/scratch/cscs/abussy/dftk_beverin/julia-1.10.10/share/julia/stdlib/v1.10/LinearAlgebra/src/lapack.jl:1668
  [3] svdvals!
    @ /capstor/scratch/cscs/abussy/dftk_beverin/julia-1.10.10/share/julia/stdlib/v1.10/LinearAlgebra/src/svd.jl:217 [inlined]
  [4] svdvals(A::ROCArray{Float64, 2, AMDGPU.Runtime.Mem.HIPBuffer})
    @ LinearAlgebra /capstor/scratch/cscs/abussy/dftk_beverin/julia-1.10.10/share/julia/stdlib/v1.10/LinearAlgebra/src/svd.jl:242
  [5] cond(A::ROCArray{Float64, 2, AMDGPU.Runtime.Mem.HIPBuffer}, p::Int64)
    @ LinearAlgebra /capstor/scratch/cscs/abussy/dftk_beverin/julia-1.10.10/share/julia/stdlib/v1.10/LinearAlgebra/src/dense.jl:1556
  [6] cond(A::ROCArray{Float64, 2, AMDGPU.Runtime.Mem.HIPBuffer})
    @ LinearAlgebra /capstor/scratch/cscs/abussy/dftk_beverin/julia-1.10.10/share/julia/stdlib/v1.10/LinearAlgebra/src/dense.jl:1555
  [7] (::DFTK.AndersonAcceleration)(xₙ::ROCArray{…}, αₙ::Float64, Pfxₙ::ROCArray{…})
    @ DFTK /capstor/scratch/cscs/abussy/dftk_beverin/DFTK.jl/src/scf/anderson.jl:81
```

This PR overwrites LAPACK's `gesdd!` (divide and conquer SVD) method with rocSOLVER's `gesvd!` (generic SVD) for ROCArrays. This is a temporary workaround until AMDGPU is fixed upstream (see )

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ffb3480e7ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.