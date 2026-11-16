# Issue

**Title:** Give the notebook tests enough static TLS headroom (backport #397)

## Description

The `notebook` job has been failing on Linux since qiskit 2.6.0 reached PyPI. `integrate_fulqrum.ipynb` and `integrate_sbd.ipynb` both die before any cell runs with `cannot allocate memory in static TLS block`. The error names qiskit's own `_accelerate.abi3.so` in one notebook and a bundled libgomp in the other. macOS is unaffected, and the `py` env passes because it installs neither Aer nor sbd-eigensolver.

glibc sizes the per-thread TLS block at startup and keeps only a small surplus for libraries `dlopen`ed afterwards that need initial-exec TLS. Every Python extension module arrives that way, so they all draw on that one surplus, and the library that fails is whichever asks last rather than whichever consumed the space — hence the same failure pointing at different libraries in different notebooks.

qiskit 2.6.0's `_accelerate` grew from 736 to 1544 bytes of initial-exec TLS, leaving too little for the next extension in the import order. The growth is `matrixmultiply` 0.3.11 enabling its AVX-512 kernels, which quadruple one thread-local scratch buffer. That path is gated on rustc >= 1.89, and 2.6.0 also raised its MSRV from 1.87 to exactly that — neither bump alone would have changed anything, it took both to compile the larger buffer in.

This raises the surplus via `GLIBC_TUNABLES`, scoped to the `notebook` env since that is the only one that runs out. The value matches the one qiskit-aer settled on for the same problem.

Reported upstream as Qiskit/qiskit#17213, with measurements. The same workaround is on sbd-eigensolver-python in Qiskit/sbd-eigensolver-python#64, where CI is green with it. Remove this once 17213 is fixed in a release.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.
<hr>This is an automatic backport of pull request #397 done by [Mergify](https://mergify.com).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb2c003aa25b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.