# Issue

**Title:** utils: declare openblas_set_num_threads weak

## Description

## What

`qp_blas_pin_pool()` calls `openblas_set_num_threads`, which only OpenBLAS
exports. As a plain `extern`, the linker insists on a definition, so any
build against reference BLAS, MKL or Accelerate fails:

```
irpf90.a(c_funcs.o): in function `qp_blas_pin_pool':
src/ao_extra_basis/utils/c_funcs.c:21: undefined reference to `openblas_set_num_threads'
FAILED: src/ao_extra_basis/{extra_basis,fit_1s_basis,write_extra_grid}
```

That is what the GitHub runner hit in
[run 43218728110](https://github.com/QuantumPackage/qp2/actions/runs/43218728110)
— it installs `libblas-dev`, whose `-lblas` is the reference BLAS. Only the
three `ao_extra_basis` programs fail because only they pull `c_funcs.o` out
of `irpf90.a`, which is why the log looks partial.

## Change

```c
extern void openblas_set_num_threads(int) __attribute__((weak));

static void qp_blas_pin_pool(void)
{
  if (openblas_set_num_threads != NULL)
    openblas_set_num_threads(1);
}
```

A weak undefined reference resolves to `NULL` when the symbol is absent, so
the object links against any BLAS and the pin still runs when the BLAS is
OpenBLAS. The null test is legal *because* the symbol is weak: with a strong
`extern` the same test warns `-Wtautological-pointer-compare`, since the
address could never be null. OpenBLAS's own `common.h` uses the identical
idiom for `omp_in_parallel`.

The return type is corrected to the real prototype: OpenBLAS declares
`void openblas_set_num_threads(int)` (`common.h`, and OpenMathLib/OpenBLAS
issue 131), not `int`.

## Evidence

Compiled for `x86_64-linux-gnu` and inspected the ELF symbol table, since
the block is `#ifdef __linux__` and cannot be exercised on the Mac:

| source | symbol table | effect |
|---|---|---|
| plain `extern` (before) | `*UND*` | hard link error when absent |
| `__attribute__((weak))` (after) | `w *UND*` | resolves to 0 |

* `-O0/-O2/-O3 -Wall -Wextra`: no warning; the guard survives into the
  object (GOT-load test plus a conditional PLT call), so the call is not
  optimised out.
* Linked against a mock library that defines the symbol: links, and the pin
  runs at startup.
* `openblas_set_num_threads` is now the only use of the symbol, so no other
  translation unit is affected.

Note: a PR targeting `qp3` triggers no workflow — the workflows filter on
`master` and `dev-stable` — so this cannot turn a check green. It was
validated at the object-file level instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6453f1b72cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.