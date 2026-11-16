# Issue

**Title:** Extract LOBPCG eigensolver into standalone LOBPCGEigensolver.jl package

## Description

Extracts the stability-focused **LOBPCG algorithm** out of `src/eigen/` into a new, dependency-light package **[LOBPCGEigensolver.jl](https://github.com/JuliaMolSim/LOBPCGEigensolver.jl)** under JuliaMolSim, which exposes the low-level `lobpcg(A, X, B, precon, tol, maxiter; …)` entry point. DFTK depends on it.

### What moved to the package
- The LOBPCG algorithm itself (formerly `lobpcg_hyper_impl.jl`).
- The GPU-only `compute_λ` helper and the AMDGPU `LinearAlgebra` workarounds (Cholesky / `gesdd!` / 5-arg `mul!`), now in `LOBPCGEigensolver`'s AMDGPU extension — loaded automatically whenever DFTK and AMDGPU are both present.
- The LOBPCG-internal unit tests.

### What stays in DFTK
- The `lobpcg_hyper` convenience wrapper (default tolerance, `converged`/`n_iter` reporting) and the dense `diag_full` reference solver — these aren't LOBPCG per se; they now call `LOBPCGEigensolver.lobpcg`.
- `diagonalize_all_kblocks` / `select_eigenpairs_all_kblocks` (the k-block driver).
- `PreconditionerTPA` / `PreconditionerNone`, which now extend `LOBPCGEigensolver.precondprep!`.
- DFTK's own `columnwise_dots` / `columnwise_norms` (used well beyond the solver).

### Timings are preserved
The solver takes the `TimerOutput` to record into as a `timer` keyword (added in , released in 0.1.1), and `lobpcg_hyper` hands it `DFTK.timer`. The solver's internal sections therefore show up in the DFTK timer exactly as before the extraction, now nested under `lobpcg_hyper`:

```
self_consistent_field
  lobpcg_hyper
    matvec
      DftHamiltonian multiplication
    ortho! X vs Y
      ortho!
    rayleigh_ritz
    preconditioning
    Update residuals
```

Since `@timing` only compiles away for DFTK's own code, the timer object itself is disabled when the `timer_enabled` preference is off, so the solver stays silent too.

### Incidental fix
`hessian.jl`'s `size(::DielectricAdjoint, ...)` now uses `Base.size` explicitly. It previously relied on an `import Base.size` that the eigensolver file happened to run at DFTK module scope; without that file, a bare `size` definition shadowed `Base.size` and broke `size(::Vector)` everywhere.

### Status
Needs **LOBPCGEigensolver 0.1.1** (the version carrying the `timer` keyword) in General: . CI can resolve once that merges. `Project.toml` carries only the `[deps]`/`[compat]` entries (no local `[sources]` override).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01HFAujBDzeangCqdQxhSbYw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59090a9fd4c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.