# Issue

**Title:** GPU optimized symmetry operations

## Description

When simulating large systems with symmetries, the symmetrization of the density is extremely slow. This is because the array is first transferred to the CPU, before a double loop over symmetries and G vectors takes place. By comparison to loops running on the GPU, this is slow, and the operation becomes a major bottleneck.

This PR introduces GPU specific implementations for `accumulate_over_symmetries!` and `lowpass_for_symemtry!`, using the `map!` construct to run on the device, and thus saving data transfers. The loop itself is also greatly accelerated. Note that these new implementations do run on the CPU, but slower than the current solution.

For illustration, using the input below, I observe these timings (seconds):

| GPU | master | this PR |
| --- | --- |---|
| A100|  195 | 14 |
| H100 | 135 | 9 |
| Mi200 | 212 | 26|

```
using DFTK
using PseudoPotentialData
using CUDA
# using AMDGPU
setup_threading(;)

arch = DFTK.GPU(CuArray)
# arch = DFTK.CPU(ROCArray)

Ecut = 32.0
kgrid = [2, 1, 1]
maxiter = 5
tol = 1.0e-8
temperature = 1e-4

factor = 4
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

model = model_DFT(lattice, atoms, positions; temperature=temperature,
                  functionals=PBE(), smearing=DFTK.Smearing.Gaussian())

# warmup
basis  = PlaneWaveBasis(model; Ecut, kgrid, architecture=arch)
scfres = self_consistent_field(basis; maxiter=3, tol=tol);

#actual calculations
DFTK.reset_timer!(DFTK.timer)
basis  = PlaneWaveBasis(model; Ecut, kgrid, architecture=arch)
scfres = self_consistent_field(basis; maxiter=maxiter, tol=tol);
@show DFTK.timer
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `858f73d55abf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.