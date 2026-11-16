# Issue

**Title:** Optimize response for GPUs

## Description

This PR optimizes the response code for GPUs. This is already very optimized, but I'd like to raise a couple of questions and collect feedback before I clean it up. My questions will mostly be relevant to @mfherbst , @niklasschmitz and @gkemlin (I think).

Here is a performance teaser, based on a band gap optimization script (see below). These are timings of the `self_consistent_field ForwardDiff` function, reported in seconds:

|  | master | this PR |
|----------|----------|----------|
| CPU  | 4640  | 4104  |
| H100  | 780  | 69  |
| Mi250  |850  | 125 |

The main aspects of this PR are:
- Vectorization of the CG solver: currently, a different CG solver is applied to each band. This is not ideal for GPUs, which perform much better on larger arrays. This PR generalizes the CG solver for matrix input (also helps with BLAS threading)
- Usage of buffers in the projections. Currently the [projectors](https://github.com/JuliaMolSim/DFTK.jl/blob/af5f56a0909ffadc655c17ba5924246acdb57092/src/response/chi0.jl#L127-L135) allocate a lot of memory, especially because they are nested in each other, and called many times over. This PR introduces in-place projectors  that avoid memory allocations
- Optimization of Sternheimer solver setup. Right before the solver is called, nbands^2 column-wise operations [take place](https://github.com/JuliaMolSim/DFTK.jl/blob/af5f56a0909ffadc655c17ba5924246acdb57092/src/response/chi0.jl#L362-L375). This is very slow on the GPU, and this PR replaces it with a single linear algebra call

There are no fundamental changes, but I have a few questions:

- [ ] There are 2 functions that seem to do the same thing: `solve_ΩplusK` and `solve_ΩplusK_split`. I focused on the latter since it is the one used in response.  Should both exist? Should I also optimize the former?
- [ ] I duplicated the CG solver and left the current one that takes a `LinearMap`. Does keeping it make any sense, or should I adapt the existing code calling the CG solver to use the vectorized version?
- [ ] In `chi0.jl`, a [`R_ldiv!`](https://github.com/JuliaMolSim/DFTK.jl/blob/af5f56a0909ffadc655c17ba5924246acdb57092/src/response/chi0.jl#L180-L182) function is defined. It involves 2 nested projections R: `x .= R(precon \ R(y))`. I have a feeling the projection of `y` is redundant. In fact, I pass all the tests when removing it. Is there a good theoretical reason it should stay?
- [ ] In the [current code](https://github.com/JuliaMolSim/DFTK.jl/blob/af5f56a0909ffadc655c17ba5924246acdb57092/src/response/chi0.jl#L378-L379), there is one `tol` per band. Is that necessary?
- [ ] The current CG solver has MPI support, is that necessary? 

Benchmark script for above table:
```
using DFTK, PseudoPotentialData
using ForwardDiff, Optimization # version 4.8.0 required
using CUDA

function gaas_band_gap(a)
    @show a
    lattice = a * [1 0 0; 0 1 0; 0 0 1]
    pseudopot = PseudoFamily("dojo.nc.sr.pbe.v0_4_1.stringent.upf")
    Ga = ElementPsp(:Ga, pseudopot)
    As = ElementPsp(:As, pseudopot)
    atoms = [Ga, Ga, Ga, Ga, As, As, As, As]
    positions = [[0.00, 0.00, 0.00],
                 [0.00, 0.50, 0.50],
                 [0.50, 0.00, 0.50],
                 [0.50, 0.50, 0.00],
                 [0.25, 0.75, 0.75],
                 [0.25, 0.25, 0.25],
                 [0.75, 0.75, 0.25],
                 [0.75, 0.25, 0.75],
]
    model = model_DFT(lattice, atoms, positions; functionals=PBE(), temperature=1e-3)
    basis = PlaneWaveBasis(model; Ecut=32, kgrid=(3, 3, 3), architecture=DFTK.GPU(CuArray))
    @show basis.kcoords_global[1]
    scfres = self_consistent_field(basis; tol=1e-6)
    εг = scfres.eigenvalues[1] # Extract eigenvalues at П-point 
    vbm = maximum(εг[εг.≤ scfres.εF])
    cbm = minimum(εг[εг.> scfres.εF])
    @show cbm  - vbm
    band_gap = cbm  - vbm
end

a_original = 10.55 # GaAs lattice constant in bohrs
Eg_target = 0.015 # Target band gap in Hartree
band_gap_loss(a, p) = (Eg_target - gaas_band_gap(a[1]))^2
optf = OptimizationFunction(band_gap_loss, AutoForwardDiff())
prob = OptimizationProblem(optf, [a_original])
#warm-up
sol = solve(prob, Optimization.LBFGS(); maxiters=1, x_tol=1e-3, allow_f_increases=true, show_trace=true)
DFTK.reset_timer!(DFTK.timer)
t = @time begin
    sol = solve(prob, Optimization.LBFGS(); maxiters=10, x_tol=1e-3, allow_f_increases=true, show_trace=true)
end
println("Optimized design lattice constant: ", sol.u[1], "in ", t, "seconds") # 10.549
@show DFTK.timer
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20c77fb25cf6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.