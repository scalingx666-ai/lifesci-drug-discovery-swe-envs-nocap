# Issue

**Title:** Fix zero-FPS GIF export crash

## Description

The Player tool accepts 0 FPS, but GIF export calculates its centisecond
delay as `100 / std::min(fps, 100)`. Exporting at zero therefore crashes with
integer division by zero. Negative input is also clamped to zero.

Require at least 1 FPS in the frame-rate control, preserving the default of
5 FPS, the maximum of 1000 FPS, and existing GIF upper-rate handling. Add
PlayerTool regressions through the existing static-plugin test binary for
zero/negative input and the default/supported rates. This applies on top of
the merged export refactoring in #3236.

Validation on Linux (Ubuntu WSL, GCC 15.2, Qt 6.10.2):

- Complete default CMake build passed.
- All 134 configured CTest groups passed, including 16 QtPlugins groups.
  Test data: avogadrodata `67ab090`. Twenty individual cases were conditionally
  skipped for optional tools, locales, platform-specific or non-applicable
  cases. Optional libmsym, spglib and plotting were disabled.
- The nonpositive-input regression fails with the original control range.
- An automated diagnostic invoking the actual export flow reproduced a
  floating-point exception before the fix. Afterward, requesting 0 FPS was
  clamped to 1 and produced a readable 64x64, two-frame GIF. This supplementary
  diagnostic is outside the patch; one dialog-automation run timed out and
  its retry passed.
- Both PlayerTool tests passed with ASan/UBSan instrumentation on the changed
  production and test translation units; dependencies were not instrumented.
- New-test formatting and `git diff --check` passed. clang-tidy and cppcheck
  reported findings in unchanged code/headers, none on the changed line or
  new tests; cppcheck is not a clean full-project result.

To reproduce the configured tests after configuring an in-tree build with
`ENABLE_TESTING=ON`, `BUILD_STATIC_PLUGINS=ON`, Qt/OpenGL enabled and
`AVOGADRO_DATA_ROOT` pointing to a current avogadrodata checkout:

```sh
cmake --build <build-dir> --parallel 3
ctest --test-dir <build-dir> -R '^QtPlugins-PlayerTool$' --output-on-failure
env -u QT_QPA_PLATFORM LIBGL_ALWAYS_SOFTWARE=1 \
  ctest --test-dir <build-dir> --parallel 3 --output-on-failure
```

AI tools assisted debugging, the one-line fix, test scaffolding and validation; I reviewed and approved the changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04cdc97e8d92`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.