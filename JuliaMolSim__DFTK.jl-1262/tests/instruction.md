# Issue

**Title:** Optimizing XC instantiation for GPUs

## Description

This PR optimizes the instantiation of the XC term on the GPU, with a particularly large impact when Duals are involved (stress and response calculations). It follows the same design patterns as #1163.

Particular care was given to the `hankel` function in `workarounds/forwarddiff_rules.jl`, in order to make it GPU compatible. A side effect is the suppression of allocations, which also marginally (few %) speeds-up Xc instantiation on the CPU.

For illustration, here are XC instantiation timings for the input below (stress of a 3x3x3 rattled aluminium supercell):

| | master | this PR |
|----------|----------|----------|
| A100 | 65 s | 2 s |
| Mi250 | 66 s | 2 s |

```
using DFTK
using PseudoPotentialData
using CUDA
setup_threading()

arch = DFTK.GPU(CuArray)

Ecut = 50.0
kgrid = [1, 1, 1]
maxiter = 10
tol = 1.0e-10
temperature = 0.01

factor = 3
a = 3.8267
lattice = factor*a * [[0.0 1.0 1.0];
                      [1.0 0.0 1.0];
                      [1.0 1.0 0.0]]
Al = ElementPsp(:Al, PseudoFamily("dojo.nc.sr.pbe.v0_4_1.stringent.upf"))
atoms = [Al for i in 1:factor^3]
positions = Vector{Vector{Float64}}([])
for i = 1:factor, j = 1:factor, k=1:factor
   push!(positions, [i/factor, j/factor, k/factor])
end

#rattle a few atoms                                                                                  
positions[5] = positions[5] + [0.01, 0.0, -0.01]
positions[10] = positions[10] + [0.01, 0.0, -0.01]
positions[15] = positions[15] + [0.01, 0.0, -0.01]
positions[20] = positions[20] + [0.01, 0.0, -0.01]
positions[25] = positions[25] + [0.01, 0.0, -0.01]

model = model_DFT(lattice, atoms, positions; temperature=temperature,
                  functionals=PBE(), smearing=DFTK.Smearing.Gaussian())
                  
# warmup
basis  = PlaneWaveBasis(model; Ecut, kgrid, architecture=arch)
scfres = self_consistent_field(basis; maxiter=3, tol=tol);
forces = compute_forces(scfres)
stress = compute_stresses_cart(scfres)

#actual calculations
DFTK.reset_timer!(DFTK.timer)
basis  = PlaneWaveBasis(model; Ecut, kgrid, architecture=arch)
scfres = self_consistent_field(basis; maxiter=maxiter, is_converged=ScfConvergenceEnergy(tol))
forces = compute_forces(scfres)
stress = compute_stresses_cart(scfres)
@show DFTK.timer
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc20ea20ef4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.