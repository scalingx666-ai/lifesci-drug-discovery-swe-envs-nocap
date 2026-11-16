# Issue

**Title:** Build and validate static release binaries across five platforms

## Description

This PR extends the bleeding-edge release workflow to produce validated release archives for all major supported platforms:

| Platform | Toolchain / backend | Release validation |
| --- | --- | --- |
| Linux x86_64 | ifx 2025.2 / static MKL | Fully static ELF; no `PT_INTERP` or `DT_NEEDED` |
| Linux aarch64 | GCC / static OpenBLAS | Fully static ELF; no `PT_INTERP` or `DT_NEEDED` |
| macOS arm64 | GCC / static OpenBLAS | Correct architecture; Apple system libraries only |
| macOS x86_64 | GCC / static OpenBLAS | Correct architecture; Apple system libraries only |
| Windows x86_64 | UCRT64 GCC / static OpenBLAS | No GNU, Fortran, OpenMP, pthread, BLAS, or LAPACK runtime DLL imports |

The normal compiler/test matrix now gates all release builds through a `tests-passed` job. Release jobs therefore only build and install the release configuration, inspect the final executable's linkage, package it, and upload the resulting artifact. Scientific correctness remains covered by the normal test matrix rather than being duplicated in the packaging jobs.

The generated bleeding-edge artifacts are:

- `xtb-bleed-linux-x86_64-ifx-mkl.tar.xz`
- `xtb-bleed-linux-aarch64-openblas.tar.xz`
- `xtb-bleed-macos-arm64-openblas.tar.xz`
- `xtb-bleed-macos-x86_64-openblas.tar.xz`
- `xtb-bleed-windows-x86_64-openblas.zip`
- `xtb-bleed.tar.xz`

Compiler coverage is updated at the same time:

- GCC/GFortran 10 and 11 on Ubuntu 22.04
- GCC/GFortran 12 and 13 on Ubuntu 24.04
- GCC/GFortran 14–16 on current Linux runners, with GCC 15/16 explicitly tested on Ubuntu 26.04
- existing Linux ARM and macOS GNU coverage
- native MinGW testing on Windows
- legacy `ifort`/`icc` coverage on Ubuntu 24.04
- current `ifx`/`icx` 2026.2 coverage with both CMake and Meson

Intel repository setup is updated to use a signed keyring instead of the deprecated `apt-key` path. The Meson `_Float128` compatibility workaround is also made conditional for Intel LLVM, while the `ifx` Meson test remains in precise floating-point mode for numerical reproducibility.

Bundled dependency revisions are updated.

Continuous delivery remains restricted to pushes to upstream `main`. Before publishing, the workflow requires the complete source and binary artifact set, generates SHA256 checksums, updates the `bleed` tag and release, removes the obsolete legacy Linux/Windows asset names after the new uploads succeed, and finally downloads the published artifacts again to verify their checksums and the `bleed` tag SHA.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `130708f060e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.