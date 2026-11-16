# Issue

**Title:** Remove XC GPU logic

## Description

The latest updates to Libxc.jl and DftFunctionals.jl implement CPU fallbacks when there is no GPU alternative (usual transfer from GPU to CPU, evaluation on the CPU, transfer back). Therefore, there is no need for it in DFTK anymore.

However, I ran into an unforseen issue: `MethodError` start appearing due to ambiguous signature, e.g.:

```
potential_terms(::DFTK.LibxcFunctional{:lda, :x}, ::CUDACore.CuArray{Float64, 2, CUDACore.DeviceMemory})
```

Is ambiguous because of the following 2 definitions:
```
     potential_terms(func::DFTK.LibxcFunctional{:lda}, ρ::AbstractMatrix{Float64})
       @ DFTK /capstor/scratch/cscs/abussy/dftk_santis/DFTK.jl/src/DispatchFunctional.jl:108
       
     potential_terms(func::DftFunctionals.Functional{:lda}, ρ::GPUArraysCore.AbstractGPUArray)
       @ DftFunctionals /capstor/scratch/cscs/abussy/dftk_santis/.julia/packages/DftFunctionals/j8Gg9/src/gpu.jl:26
```

Because either option has either a stronger type for the functional or the array, it's ambiguous. A method for `LibxcFunctional` and `AbstractGPUArray` must be available to resolve that.

I solved this with constructs of the type:
```
DftFunctionals.potential_terms(func::LibxcFunctional{:lda},
                               ρ::Matrix{Float64}) =
    _potential_terms(func, ρ)
DftFunctionals.potential_terms(func::LibxcFunctional{:lda},
                               ρ::AbstractGPUMatrix{Float64}) =
    _potential_terms(func, ρ)
function _potential_terms(func::LibxcFunctional{:lda},
                          ρ::AbstractMatrix{Float64})
    s_ρ, n_p = size(ρ)
    fun = Libxc.Functional(func.identifier; n_spin=s_ρ)
    derivatives = filter(in(Libxc.supported_derivatives(fun)), 0:1)
    terms = Libxc.evaluate(fun; rho=ρ, derivatives)
    e  = libxc_energy_density(terms, ρ)
    Vρ = reshape(terms.vrho, s_ρ, n_p)
    (; e, Vρ)
end
```

I don't particularly like that: it's very verbose, and seems like a step sideways instead of forward. However, I couldn't think of anything better. Suggestions are welcome.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a39b3950aa5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.