# Issue

**Title:** KernelAbstractions for FFTs

## Description

Careful GPU profiling shows that a lot of time is wasted reshuffling arrays during K-point specific FFT calls. Since FFTs are a large part of `DftHamiltonian multiplication` and `compute_density`, accelerating them can have a large impact on performance, especially for systems with dense k-point meshes.

For illustration, a `ifft!` call currently looks like this in the profiler:

![fft_master](https://github.com/user-attachments/assets/488198c0-d4cc-4133-be81-d047165f89f9)

The 3 blue squares on the right are the actual FFT, and the blue square on the left is the kernel filling the array with zeros. All the rest, i.e. the majority of the runtime, is spend in this operation: `f_real[Gvec_mapping] = f_fourier`. Something similar happens for `fft!`.

This PR introduces explicit GPU kernels for the reshuffling of data during FFTs. The `KernelAbstractions.jl` package is used in order to remain vendor agnostic (already an indirect dependency of DFTK through GPU packages). The kernel themselves are very simple, but their performance is much better. The same `ifft!` call now looks like the following in the profiler:

![fft_kernel](https://github.com/user-attachments/assets/69fa3675-9601-4c0f-8728-5807209f569b)

For this to be possible, some light code uglification is necessary. The `Gvec_mapping` field of a given K-point must be available on the GPU at all time, and transferring it to the device at each call would defeat the purpose of this PR. As a solution for this, I added a `Gvec_mapping_gpu` field to the K-point struct (could also be called `Gvec_mapping_fft`). I decided to duplicate the data rather than moving the original `Gvec_mapping` field to the device, because the latter is assumed to be on the CPU in most places in the code, and it's inverse `mapping_inv` is not in a format suitable for the GPU (and it makes sense that back and forth ops are stored in the same manner).

Finally, here are some timings (s) for the input show below:

| GPU | master | this PR |
| --- | --- |--- |
| A100 | 44 | 33 |
| H100 | 51 | 40 |
|Mi200 |71 | 54 |

```
using DFTK
using PseudoPotentialData
using CUDA
setup_threading(;)

arch = DFTK.GPU(CuArray)

Ecut = 72.0
kgrid = [10, 10, 10] 
temp = 0.01
tol = 1.0e-8
maxiter = 10

a = 7.260
lattice = a * [[1. 0. 0.];
               [0. 1. 0.];
               [0. 0. 1.]]

Sr = ElementPsp(:Sr, PseudoFamily("dojo.nc.sr.pbe.v0_4_1.stringent.upf"))
V = ElementPsp(:V, PseudoFamily("dojo.nc.sr.pbe.v0_4_1.stringent.upf"))
O = ElementPsp(:O, PseudoFamily("dojo.nc.sr.pbe.v0_4_1.stringent.upf"))

atoms     = [Sr, V, O, O, O]
positions = [[0.5, 0.5, 0.5],
             [0.0, 0.0, 0.0],
             [0.5, 0.0, 0.0],
             [0.0, 0.5, 0.0],
             [0.0, 0.0, 0.5]]

model = model_DFT(lattice, atoms, positions; temperature=temp, functionals=PBE(),
                  smearing=DFTK.Smearing.Gaussian())

#warmup
basis  = PlaneWaveBasis(model; Ecut, kgrid, architecture=arch)
scfres = self_consistent_field(basis; tol=tol, maxiter=3);

#actual calculations
DFTK.reset_timer!(DFTK.timer)
basis  = PlaneWaveBasis(model; Ecut, kgrid, architecture=arch)
scfres = self_consistent_field(basis; tol=tol, maxiter=maxiter);
@show DFTK.timer
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c035bce0c0c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.