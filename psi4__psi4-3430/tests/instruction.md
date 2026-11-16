# Issue

**Title:** libpsio: modernize config.h constants + add round-trip test

## Description

## Description

Non-breaking internal modernization of `libpsio`, plus the behavior gate the library never had. First slice of the plan in #3429.

Two things only: `config.h`'s preprocessor macros become `inline constexpr int`, and a standalone round-trip test is added and wired into `ctest`.

An earlier revision of this PR also removed the C `psio_*` free-function API. **That has been dropped.** As the analogous libiwl PR (#3428) showed, those free functions are public API that downstream plugins call directly (e.g. `v2rdm_casscf`), so removing them breaks the ecosystem build; and unlike libiwl's range-for `IWLReader`, they are no worse than the verbose `_default_psio_lib_->...`, so there was little upside to forcing the migration. Any future C-API change needs to be coordinated with downstream plugin updates rather than done unilaterally.

The deeper internal rewrites from #3429 — `AIOHandler` single job-queue, `psio_ud`/TOC/`char*`-path/fd-RAII — remain follow-ups that want this test as a safety net first. The multi-volume striping removal is #3452, stacked on this PR.

## User API & Changelog headlines
- [ ] No user-visible change. `psio_error()`'s public signature is unchanged (error codes stay `int` rather than becoming an `enum class`), so there is no downstream impact.

## Dev notes & details
- [ ] `config.h`: `#define` → `inline constexpr int` for `PSIO_KEYLEN`, `PSIO_MAXUNIT`, `PSIO_PAGELEN`, `PSIO_MAXVOL` and the `PSIO_ERROR_*` codes. Same names, same values. Gives the constants a type, a scope, and debugger visibility.
- [ ] New `psi4/src/psi4/libpsio/test/`: a standalone round-trip exerciser. Writes then reads back four entries whose sizes deliberately straddle the branches of `PSIO::rw` — 64 B (sub-page partial), exactly `PSIO_PAGELEN` (one full page, no remainder), `3 * PSIO_PAGELEN + 137` (multiple full pages plus a trailing partial), and 8 B.
- [ ] The test links a curated subset of static archives (`psio psi4util options ciomr`) plus a small `stubs.cc` supplying the runtime globals normally provided by `core.cc`. No Python, no libdpd, no libmints/Libint closure.
- [ ] Not built on Windows. The curated link line resolves under GNU/Clang but not clang-cl/lld-link, which emits inline and implicit functions that GCC discards as unused: `psio.lib` ends up referencing `DPDMOSpace::~DPDMOSpace` (via `std::vector<DPDMOSpace>` in `dpd.h`), and `psi4util.lib` references `Molecule::Molecule(const Molecule&)` (inline `Molecule::clone`, `molecule.h:200`) and `ExternalPotential::print` (inline `py_print`, `extern.h:131`). Not a unity or PCH artifact — Linux is unity-built too and its archives carry no such references, and Azure Windows builds with PCH off. (An earlier revision of this description blamed the unity build; that was wrong.)
- [ ] Labelled `"psi;quicktests;smoketests;libpsio"`. `quicktests` alone only reached the GH macOS lane; the Azure lanes drive ctest by `-L "plug|smoke"` (`devtools/scripts/ci_run_test.py`) and `--label-regex smoke`. Verified the test is selected by all three selectors.
- [ ] Fixed the `DPD` stub to declare `file4_cache_del_filenum(std::size_t)`, matching `dpd.h:483`. It previously said `unsigned long`, which mangles differently on Windows x64 — that accounted for one of the four undefined symbols above.
- [ ] Registration lives in the superbuild (`tests/libpsio/`), not next to the executable. `psi4-core` is configured as a separate `ExternalProject` with its own binary directory and never calls `enable_testing()`, so an `add_test()` under `psi4/src/` generates no `CTestTestfile.cmake` at all — and CI invokes `ctest` from the superbuild directory, which cannot descend into the core build tree in any case. Resolving the ExternalProject's `BINARY_DIR` from `tests/` makes `ctest -L quick` actually execute it.

## Questions
- [ ] `tests/CMakeLists.txt` gains an `add_subdirectory(libpsio)` under "Add internal projects". #3426 adds `add_subdirectory(libiwl)` at the same spot, so whichever of the two lands second will need a one-line conflict resolution. Happy to introduce a shared `add_core_unit_test()` macro in `cmake/TestingMacros.cmake` instead if you would rather have one entry point for C++ unit tests.
- [ ] Is skipping the unit tests on Windows acceptable, or would you prefer the executables link against the full closure so they run everywhere?

## AI
- [ ] Claude (Opus 4.8) assisted with the mechanical `#define` → `inline constexpr` conversion, drafting the round-trip test and its stubs, and diagnosing the ctest-registration and Windows-link problems. Reviewed and submitted by me; I am happy to answer questions about any of it.

## Checklist
- [x] Tests added for any new features — this PR *is* the test
- [x] Docstring or narrative docs/sphinxman/source updated if needed — n/a, internal only
- Verified locally: `ctest -R libpsio-roundtrip` passes, and reports failure when the binary is removed. Before the registration fix, `ctest -N -R psio_roundtrip` listed no tests at all.

## Status
- [x] Ready for review

---

Thanks @TiborGY — you were right on both counts. The description was stale, and the ctest never ran.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1496b4e98ebb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.