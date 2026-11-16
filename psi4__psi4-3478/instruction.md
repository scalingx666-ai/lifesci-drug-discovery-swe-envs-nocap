# Issue

**Title:** Thread the density-fitted and one-electron nuclear-Hessian integral loops

## Description

## What

The analytic nuclear Hessian evaluated most of its integral work **serially on a single core**, even though the sibling gradient code has long been threaded. This PR threads those loops, mirroring the established `DFJKGrad::compute_gradient` pattern (per-thread integral engines + a parallel loop over auxiliary/primary shells, with per-thread accumulators reduced afterwards). No math changes — only parallelization.

Threaded regions:

1. **DF two-electron second-derivative Hessian** (`DFJKGrad::compute_hessian`, `jk_grad.cc`) — the dominant cost. All five auxiliary-shell loops (the `(A|mn)` build, the first/second-derivative `(A|mn)^x`/`(A|mn)^xy` loops, and the metric `(A|B)^x`/`(A|B)^xy` loops) now run in parallel. Loops writing aux-partitioned intermediates are race-free by construction; the deriv1 K-scratch is made per-thread; the two `compute_shell_deriv2` loops accumulate into per-thread `JHess`/`KHess` reduced into `hessians_` before the serial tail.

2. **DF orbital-response (CPHF) perturbed-Fock build** (`RSCFDeriv::hessian_response` + `USCFDeriv::JK_deriv1`, `response.cc`) — the `(A|mn)` build plus the metric and main `(A|mn)^x` contraction loops. These scatter into per-perturbation Fock matrices keyed by shell centers (not partitioned by P), so each thread scatters into a **private copy of the perturbation batch** that is reduced afterwards. The batch size `max_a` is re-budgeted so the per-thread copies fit inside the memory budget (`df_mem / ((1+nthreads)·nso²)`, capped at `3·natom`).

3. **One-electron Hessian terms** (`SCFDeriv::compute_hessian`, `scf_grad.cc`) — the Potential, Kinetic, and Overlap shell-pair loops, with per-thread one-electron engines and a per-thread accumulator. (ECP left serial — rare, differently structured.)

## Bonus bug fix

While threading (2), fixed a **pre-existing latent fault** in the multi-batch response path: the loops mark a whole atom in-core when *any* of its perturbations falls in a batch and then write all three of its Fock derivatives, so a batch boundary that split an atom wrote into an unmapped accumulator (segfault). `max_a` is now forced to a multiple of 3 (atom-aligned).

## Validation

Analytic DF Hessians (def2-SVP, `scf_type df`) computed at 1 vs 6 threads, RHF and UHF:

- Small molecules (H2O, NH2), single batch: agreement to **1e-10 … 6e-10**.
- Multi-batch reduction isolated at fixed thread count (single vs multi batch): **~7e-9** — the same magnitude as two *identical* runs of the same configuration (**~1e-8** for a water tetramer), i.e. pure floating-point summation-order noise from the threaded reduction (dynamic scheduling), not a correctness difference. This is the same run-to-run nondeterminism already present in psi4's other threaded quadrature/JK code, and is physically negligible for a Hessian.

Normal-memory runs use a single batch (`max_a` capped at `3·natom`), so results there are identical to the previous serial code up to threading FP noise; existing Hessian tests are unaffected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ddd0b3a85d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.