# Issue

**Title:** Dispatch Dual GEMM to BLAS

## Description

As mentioned in #1387, calculating stress tensors of large systems reveals new bottlenecks. One of them is `ene_ops: nonlocal` with the Dual basis. It turns out that GEMM with matrices of Duals are not dispatched to BLAS, because only matrices of BlasFloat are. Instead, a generic Julia implementation is used. This PR introduces a workaround that splits matrices of Duals into their values and partial, and does all the GEMM individually with BLAS compatible matrices.

When running on GPUs, the effect on performance is huge. Here are timings for a 216 atoms rattled aluminium system:

With master:
```
compute_stresses_cart                      1    53.8s   71.8%   53.8s   5.57GiB   78.7%  5.57GiB
  PlaneWaveBasis                           6    34.9s   46.6%   5.82s   5.54GiB   78.3%   946MiB
    Instantiation Ewald                    6    22.9s   30.5%   3.81s    215KiB    0.0%  35.8KiB
      precomp: Ewald                       6    22.9s   30.5%   3.81s    207KiB    0.0%  34.5KiB
    Instantiation AtomicLocal              6    4.53s    6.0%   755ms   1.91GiB   27.0%   326MiB
    Instantiation AtomicNonlocal           6    3.76s    5.0%   627ms   1.52GiB   21.5%   259MiB
    Instantiation Xc                       6    3.62s    4.8%   604ms   1.37GiB   19.3%   233MiB
    build_kpoints                          6   53.0ms    0.1%  8.84ms    290MiB    4.0%  48.3MiB
    Instantiation Hartree                  6   2.62ms    0.0%   437μs   62.0KiB    0.0%  10.3KiB
    Instantiation Kinetic                  6   1.78ms    0.0%   297μs   81.3KiB    0.0%  13.5KiB
    Instantiation PspCorrection            6    405μs    0.0%  67.5μs   9.09KiB    0.0%  1.52KiB
    Instantiation Entropy                  6   47.5μs    0.0%  7.91μs     0.00B    0.0%    0.00B
  energy                                   6    18.5s   24.7%   3.08s   2.82MiB    0.0%   482KiB
    ene_ops: nonlocal                      6    18.4s   24.6%   3.07s    106KiB    0.0%  17.7KiB
    energy: xc                             6   34.4ms    0.0%  5.73ms   1.61MiB    0.0%   275KiB
    ene_ops: kinetic                       6   10.0ms    0.0%  1.67ms    145KiB    0.0%  24.2KiB
    ene_ops: hartree                       6   5.93ms    0.0%   988μs    423KiB    0.0%  70.6KiB
    ene_ops: local                         6   1.73ms    0.0%   288μs   94.0KiB    0.0%  15.7KiB
  compute_density                          6    417ms    0.6%  69.5ms   26.5MiB    0.4%  4.41MiB
    symmetrize_ρ                           6   5.60ms    0.0%   933μs    344KiB    0.0%  57.3KiB
```

With this PR:
```
compute_stresses_cart                      1    31.9s   58.9%   31.9s   5.57GiB   78.6%  5.57GiB
  PlaneWaveBasis                           6    31.0s   57.3%   5.17s   5.54GiB   78.1%   946MiB
    Instantiation Ewald                    6    22.8s   42.2%   3.80s    215KiB    0.0%  35.8KiB
      precomp: Ewald                       6    22.8s   42.2%   3.80s    207KiB    0.0%  34.5KiB
    Instantiation Xc                       6    2.91s    5.4%   485ms   1.37GiB   19.3%   233MiB
    Instantiation AtomicLocal              6    2.76s    5.1%   460ms   1.91GiB   26.9%   326MiB
    Instantiation AtomicNonlocal           6    2.45s    4.5%   408ms   1.52GiB   21.4%   259MiB
    build_kpoints                          6   50.4ms    0.1%  8.40ms    290MiB    4.0%  48.3MiB
    Instantiation Hartree                  6   2.57ms    0.0%   429μs   62.3KiB    0.0%  10.4KiB
    Instantiation Kinetic                  6   1.44ms    0.0%   240μs   81.3KiB    0.0%  13.5KiB
    Instantiation PspCorrection            6    338μs    0.0%  56.3μs   9.09KiB    0.0%  1.52KiB
    Instantiation Entropy                  6   24.8μs    0.0%  4.13μs     0.00B    0.0%    0.00B
  energy                                   6    486ms    0.9%  80.9ms   3.03MiB    0.0%   518KiB
    ene_ops: nonlocal                      6    416ms    0.8%  69.4ms    325KiB    0.0%  54.2KiB
    energy: xc                             6   34.9ms    0.1%  5.81ms   1.61MiB    0.0%   275KiB
    ene_ops: kinetic                       6   26.1ms    0.0%  4.36ms    145KiB    0.0%  24.2KiB
    ene_ops: hartree                       6   6.22ms    0.0%  1.04ms    423KiB    0.0%  70.6KiB
    ene_ops: local                         6   1.39ms    0.0%   232μs   94.3KiB    0.0%  15.7KiB
  compute_density                          6    355ms    0.7%  59.1ms   26.3MiB    0.4%  4.38MiB
    symmetrize_ρ                           6   4.55ms    0.0%   758μs    344KiB    0.0%  57.3KiB
```

`ene_ops: nonlocal` goes from 18.5 seconds to ~400 ms, and the bottleneck disappears. Note that the huge time spent in `Instantiation Ewald` is taken care of in #1388.

This PR also improves timings on the CPU, for all system sizes. On average, `ene_ops: nonlocal` is ~2x faster then on master. Basis instantiation remains the overall bottleneck on CPU nevertheless.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a55c25ec8c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.