# Issue

**Title:** Reduce Ewald summation work with pair-specific image bounds

## Description

Cf  I haven't checked any of it, but the basic idea appears right.

AI slop follows.





Ewald setup evaluates every atom pair over a global box of periodic images, including many whose screened interaction is negligible. Bound the images separately for each pair and apply the real- and reciprocal-space spherical cutoffs before evaluating the expensive terms. This addresses the bottleneck discussed in #1387.

The real-space loop now updates Cartesian separations incrementally and converts accumulated Cartesian forces to reduced coordinates once per atom. It also uses the analytical radial derivative and accumulates energy per atom to reduce roundoff. The default η and full ordered pair sum are unchanged. Complex phonon displacements are included in the image bounds; their derivatives still use the complex-analytic distance.

This also fixes the ordinary `energy_forces_ewald` wrapper silently discarding the supplied η.

### CPU timings

216 Al ions in a 6×6×6 FCC primitive supercell, lattice parameter 4.05 Å, Julia 1.12.4, Alder Lake CPU. This is a representative system; #1387 does not provide its complete benchmark input.

| Implementation | Float64 Ewald call | Six strain directions, Ewald only |
|---|---:|---:|
| Master | 2.24 s | 20.55 s |
| #1387 at 665d82428a | 0.83 s | 7.61 s |
| This PR | 0.080 s | 1.09 s |

Compilation is excluded. Float64 timings are minima of three warmed calls. The strain timings are the measured sum of six one-partial Dual calls, matching the Ewald work in `compute_stresses_cart`; they do not include the rest of stress evaluation. Ewald runs on the CPU even in GPU calculations. No GPU benchmark was run.

`benchmark/ewald.jl` includes the reproducer and instructions for comparing the implementations.

### Validation

- All 19 assertions in the three `energy_forces_ewald` test items pass: existing reference energies, η independence and forwarding, periodic shifts, forces, strain derivatives, and a nonzero-q complex phonon response checked against finite differences.
- Independent comparisons with the original implementation on a skew three-ion cell give force and first/second phonon-response errors below 4×10⁻¹⁴.
- The 216-atom energy agrees with 216 times the primitive-cell energy within 1.4×10⁻¹² Ha. Perturbed Al216 forces agree with the original to 4.6×10⁻¹⁴ relative error.

Targeted test command in the persistent test environment:

```julia
TestItemRunner.run_tests("test/";
    filter=ti -> startswith(ti.name, "energy_forces_ewald"))
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc968b9c4c9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.