# Issue

**Title:** share memory pools between torch and cupy

## Description

from @tvogels 

> We now have chunked evaluation that should prevent out of memory errors.
> 
> While running timing benchmarks on the public skala code, I did encounter out of memory errors for the largest molecules from the timing dataset on a 80GB A100.
> 
> The issue seems to be that both cupy and pytorch have their own memory allocator, so they eat into each other's buffer.
> 
> In my case I could resolve the OOM errors by using
> ```
> import pytorch_pfn_extras as ppe
> 
> ppe.cuda.use_torch_mempool_in_cupy()
> see https://docs.cupy.dev/en/stable/user_guide/interoperability.html#pytorch.
> ```
> This is a package we have to add to the environment.

This should fix that. @szbernat 

My agent wrote a script to profile the code to
evaluate the memory impact of enabling the PFN allocator bridge
(pytorch_pfn_extras CUDA mempool in CuPy) for the Skala GPU4PySCF gradient
workload, and compare it to the default CuPy allocator.

## Benchmark Script

The script is now intentionally limited to one built-in benchmark molecule: naphthalene.
It executes both allocator modes in isolated child processes and reports only the peak
metrics used in this comparison:
- peak_torch_alloc
- peak_torch_reserved
- peak_cupy_used
- peak_cupy_total
- peak_device_used
- elapsed time
- numerical result signature consistency

Full script:

```python
#!/usr/bin/env python3

"""Benchmark memory impact of pytorch_pfn_extras CuPy allocator hook.

This script compares two allocator modes for the same GPU workload:
1. pfn: CuPy allocator set via pytorch_pfn_extras.use_torch_mempool_in_cupy
2. cupy: CuPy default memory pool allocator

Each mode is executed in a fresh child process to avoid cross-contamination
of allocator and CUDA runtime state.
"""

from __future__ import annotations

import argparse
import gc
import json
import math
import os
import subprocess
import sys
import tempfile
import time
from dataclasses import asdict, dataclass


@dataclass
class RunStats:
    mode: str
    allocator_owner: str
    peak_torch_alloc: int
    peak_torch_reserved: int
    peak_cupy_used: int
    peak_cupy_total: int
    peak_device_used: int
    elapsed_s: float
    result_signature: float


def _mib(nbytes: int) -> float:
    return nbytes / (1024**2)


def _print_table(rows: list[RunStats]) -> None:
    print(
        "mode | owner | peak_torch_alloc(MiB) | peak_torch_reserved(MiB) | "
        "peak_cupy_used(MiB) | peak_cupy_total(MiB) | peak_device_used(MiB) | "
        "elapsed(s) | signature"
    )
    for row in rows:
        print(
            f"{row.mode} | {row.allocator_owner} | "
            f"{_mib(row.peak_torch_alloc):.2f} | {_mib(row.peak_torch_reserved):.2f} | "
            f"{_mib(row.peak_cupy_used):.2f} | {_mib(row.peak_cupy_total):.2f} | "
            f"{_mib(row.peak_device_used):.2f} | {row.elapsed_s:.2f} | {row.result_signature:.10e}"
        )


def _build_molecule(basis: str):
    from pyscf import gto

    atom = (
        "C 0.000000 1.402720 0.000000; "
        "C 1.214790 0.701360 0.000000; "
        "C 1.214790 -0.701360 0.000000; "
        "C 0.000000 -1.402720 0.000000; "
        "C -1.214790 -0.701360 0.000000; "
        "C -1.214790 0.701360 0.000000; "
        "C 2.429580 1.402720 0.000000; "
        "C 3.644370 0.701360 0.000000; "
        "C 3.644370 -0.701360 0.000000; "
        "C 2.429580 -1.402720 0.000000; "
        "H 0.000000 2.490290 0.000000; "
        "H -2.156660 1.245150 0.000000; "
        "H -2.156660 -1.245150 0.000000; "
        "H 0.000000 -2.490290 0.000000; "
        "H 2.429580 2.490290 0.000000; "
        "H 4.586240 1.245150 0.000000; "
        "H 4.586240 -1.245150 0.000000; "
        "H 2.429580 -2.490290 0.000000"
    )
    return gto.M(atom=atom, basis=basis, cart=True)


def run_child(mode: str, warmup: int, iters: int, basis: str, grid_level: int) -> RunStats:
    import cupy
    import pytorch_pfn_extras
    import torch
    from pyscf import gto

    from skala.functional import ExcFunctionalBase, load_functional
    from skala.gpu4pyscf.gradients import nuc_grad_from_veff, veff_and_expl_nuc_grad

    if not torch.cuda.is_available():
        raise RuntimeError("CUDA is not available")

    def get_grid_and_rdm1(mol: gto.Mole) -> tuple[object, torch.Tensor]:
        from gpu4pyscf import dft

        grids = dft.Grids(mol)(level=grid_level, radi_method=dft.radi.treutler).build()
        mf = dft.KS(mol, xc="pbe")(grids=grids)
        mf.kernel()
        rdm1 = torch.from_dlpack(mf.make_rdm1())  # type: ignore[attr-defined]
        return mf.grids, rdm1

    class TestFunc(ExcFunctionalBase):
        def __init__(self) -> None:
            super().__init__()
            self.features = ["grad", "grid_weights"]

        def get_exc(self, mol: dict[str, torch.Tensor]) -> torch.Tensor:
            return (
                (mol["grad"] ** 2 @ mol["grid_weights"])
                @ torch.tensor([1.0, 2.0, 3.0], dtype=torch.float64, device=mol["grad"].device)
            ).sum()

    cupy.cuda.set_allocator(cupy.get_default_memory_pool().malloc)
    torch.cuda.synchronize()
    torch.cuda.empty_cache()
    cupy.get_default_memory_pool().free_all_blocks()
    gc.collect()

    if mode == "pfn":
        pytorch_pfn_extras.cuda.use_torch_mempool_in_cupy()
    elif mode == "cupy":
        cupy.cuda.set_allocator(cupy.get_default_memory_pool().malloc)
    else:
        raise ValueError(f"Unknown mode: {mode}")

    alloc_owner = type(getattr(cupy.cuda.get_allocator(), "__self__", None)).__name__

    mol = _build_molecule(basis=basis)
    grid, rdm1 = get_grid_and_rdm1(mol)
    _ = load_functional("skala-1.1", device=torch.device("cuda:0"))
    exc_test = TestFunc()

    for _ in range(warmup):
        veff = veff_and_expl_nuc_grad(exc_test, mol, grid, rdm1, nuc_grad_feats={"grad"})[0]
        _ = 2 * nuc_grad_from_veff(mol, veff, rdm1)

    torch.cuda.synchronize()
    torch.cuda.empty_cache()
    torch.cuda.reset_peak_memory_stats()

    free0, total0 = cupy.cuda.runtime.memGetInfo()
    peak_device_used = int(total0 - free0)
    peak_cupy_used = int(cupy.get_default_memory_pool().used_bytes())
    peak_cupy_total = int(cupy.get_default_memory_pool().total_bytes())

    t0 = time.perf_counter()
    signature = 0.0
    for _ in range(iters):
        veff = veff_and_expl_nuc_grad(exc_test, mol, grid, rdm1, nuc_grad_feats={"grad"})[0]
        grad = 2 * nuc_grad_from_veff(mol, veff, rdm1)
        signature += float(grad.detach().double().sum().item())
        peak_cupy_used = max(peak_cupy_used, int(cupy.get_default_memory_pool().used_bytes()))
        peak_cupy_total = max(peak_cupy_total, int(cupy.get_default_memory_pool().total_bytes()))
        free_b, total_b = cupy.cuda.runtime.memGetInfo()
        peak_device_used = max(peak_device_used, int(total_b - free_b))
    torch.cuda.synchronize()
    elapsed_s = time.perf_counter() - t0

    peak_torch_alloc = int(torch.cuda.max_memory_allocated())
    peak_torch_reserved = int(torch.cuda.max_memory_reserved())
    peak_cupy_used = max(peak_cupy_used, int(cupy.get_default_memory_pool().used_bytes()))
    peak_cupy_total = max(peak_cupy_total, int(cupy.get_default_memory_pool().total_bytes()))
    free_f, total_f = cupy.cuda.runtime.memGetInfo()
    peak_device_used = max(peak_device_used, int(total_f - free_f))

    return RunStats(
        mode=mode,
        allocator_owner=alloc_owner,
        peak_torch_alloc=peak_torch_alloc,
        peak_torch_reserved=peak_torch_reserved,
        peak_cupy_used=peak_cupy_used,
        peak_cupy_total=peak_cupy_total,
        peak_device_used=peak_device_used,
        elapsed_s=elapsed_s,
        result_signature=signature,
    )


def run_parent(
    warmup: int,
    iters: int,
    repeats: int,
    basis: str,
    grid_level: int,
    result_rtol: float,
    result_atol: float,
) -> int:
    rows: list[RunStats] = []
    for mode in ("pfn", "cupy"):
        for rep in range(repeats):
            stats_fd, stats_path = tempfile.mkstemp(prefix="skala_pfn_stats_", suffix=".json")
            try:
                cmd = [
                    sys.executable,
                    __file__,
                    "--child-mode",
                    mode,
                    "--warmup",
                    str(warmup),
                    "--iters",
                    str(iters),
                    "--basis",
                    basis,
                    "--grid-level",
                    str(grid_level),
                    "--stats-json-file",
                    stats_path,
                ]
                proc = subprocess.run(cmd, capture_output=True, text=True)
                if proc.returncode != 0:
                    print(f"Child run failed for mode={mode} repeat={rep}", file=sys.stderr)
                    print(proc.stdout, file=sys.stderr)
                    print(proc.stderr, file=sys.stderr)
                    return proc.returncode

                with open(stats_path, "r", encoding="utf-8") as f:
                    payload = json.load(f)
                rows.append(RunStats(**payload))
            finally:
                try:
                    os.close(stats_fd)
                    os.unlink(stats_path)
                except OSError:
                    pass

    _print_table(rows)

    by_mode: dict[str, list[RunStats]] = {"pfn": [], "cupy": []}
    for row in rows:
        by_mode[row.mode].append(row)

    def max_attr(mode_rows: list[RunStats], attr: str) -> int:
        return max(int(getattr(r, attr)) for r in mode_rows)

    print("\nMaxima across repeats:")
    for attr, label in (
        ("peak_torch_alloc", "peak_torch_alloc"),
        ("peak_torch_reserved", "peak_torch_reserved"),
        ("peak_cupy_used", "peak_cupy_used"),
        ("peak_cupy_total", "peak_cupy_total"),
        ("peak_device_used", "peak_device_used"),
    ):
        pfn_max = max_attr(by_mode["pfn"], attr)
        cupy_max = max_attr(by_mode["cupy"], attr)
        print(
            f"{label}: pfn={_mib(pfn_max):.2f} MiB, cupy={_mib(cupy_max):.2f} MiB, "
            f"diff(pfn-cupy)={_mib(pfn_max - cupy_max):.2f} MiB"
        )

    pfn_sig_mean = sum(r.result_signature for r in by_mode["pfn"]) / len(by_mode["pfn"])
    cupy_sig_mean = sum(r.result_signature for r in by_mode["cupy"]) / len(by_mode["cupy"])
    diff = abs(pfn_sig_mean - cupy_sig_mean)
    tol = result_atol + result_rtol * max(abs(pfn_sig_mean), abs(cupy_sig_mean))
    print(
        "result_signature: "
        f"pfn_mean={pfn_sig_mean:.12e}, cupy_mean={cupy_sig_mean:.12e}, "
        f"abs_diff={diff:.3e}, tol={tol:.3e}"
    )
    if not math.isfinite(diff) or diff > tol:
        print("Result mismatch between allocator modes exceeds tolerance.", file=sys.stderr)
        return 2
    print("Result check passed: allocator modes are numerically consistent within tolerance.")
    return 0


def parse_args() -> argparse.Namespace:
    parser = argparse.ArgumentParser(description=__doc__)
    parser.add_argument("--child-mode", choices=["pfn", "cupy"], default=None)
    parser.add_argument("--warmup", type=int, default=2)
    parser.add_argument("--iters", type=int, default=8)
    parser.add_argument("--repeats", type=int, default=2)
    parser.add_argument("--basis", type=str, default="def2-svp")
    parser.add_argument("--grid-level", type=int, default=1)
    parser.add_argument("--result-rtol", type=float, default=1e-10)
    parser.add_argument("--result-atol", type=float, default=1e-8)
    parser.add_argument("--stats-json-file", type=str, default=None)
    return parser.parse_args()


def main() -> int:
    args = parse_args()
    if args.child_mode is not None:
        stats = run_child(args.child_mode, args.warmup, args.iters, args.basis, args.grid_level)
        payload = json.dumps(asdict(stats))
        if args.stats_json_file:
            with open(args.stats_json_file, "w", encoding="utf-8") as f:
                f.write(payload)
                f.write("\n")
        else:
            print(payload)
        return 0
    return run_parent(
        args.warmup,
        args.iters,
        args.repeats,
        args.basis,
        args.grid_level,
        args.result_rtol,
        args.result_atol,
    )


if __name__ == "__main__":
    raise SystemExit(main())
```

## Workload

Command used (sequential execution, no concurrent runs):

    micromamba run -n skala_gpu python scripts/benchmark_pfn_allocator_memory.py \
      --basis def2-tzvp \
      --grid-level 2 \
      --warmup 2 \
      --iters 6 \
      --repeats 2

## Results

### Per-run values (MiB)

| mode | repeat | peak_torch_alloc | peak_torch_reserved | peak_cupy_used | peak_cupy_total | peak_device_used | elapsed (s) |
|---|---:|---:|---:|---:|---:|---:|---:|
| pfn  | 1 | 1233.48 | 1286.00 | 0.00 | 0.00 | 2567.56 | 49.89 |
| pfn  | 2 | 1233.48 | 1286.00 | 0.00 | 0.00 | 2567.56 | 49.88 |
| cupy | 1 | 303.87  | 360.00  | 9.16 | 1257.36 | 2917.56 | 49.77 |
| cupy | 2 | 303.87  | 360.00  | 9.16 | 1257.36 | 2917.56 | 50.14 |

### Maxima across repeats (MiB)

| metric | pfn | cupy | diff (pfn-cupy) |
|---|---:|---:|---:|
| peak_torch_alloc | 1233.48 | 303.87 | +929.61 |
| peak_torch_reserved | 1286.00 | 360.00 | +926.00 |
| peak_cupy_used | 0.00 | 9.16 | -9.16 |
| peak_cupy_total | 0.00 | 1257.36 | -1257.36 |
| peak_device_used | 2567.56 | 2917.56 | -350.00 |

Numerical consistency check:
- result signatures match within tolerance
- abs_diff = 5.062e-10
- tol = 1.256e-08

## Conclusions

1. Enabling PFN shifts allocation ownership from CuPy to Torch:
   - Torch peaks increase substantially.
   - CuPy pool growth is essentially eliminated.
2. For global device memory minimization, PFN is favorable in this workload:
   - peak_device_used is lower by about 350 MiB.
3. Numerical behavior remains consistent across allocator modes.

## Smoke Test

A lightweight allocator smoke test was added to:
- tests/test_gpu4pyscf_gradients.py

The smoke test:
- runs both allocator modes on a small HF workload
- checks numerical signature consistency between modes
- verifies that peak device memory measurements are finite and non-zero

graphics card was my local one
```NVIDIA-SMI 595.61     NVIDIA RTX PRO 2000   Driver Version: 595.95         CUDA Version: 13.2```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1e19ddb11d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.