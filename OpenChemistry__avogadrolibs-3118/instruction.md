# Issue

**Title:** Fix readability-container-size-empty warnings in avogadro/io

## Description

Takes the **`readability-container-size-empty`, `avogadro/io`** box of #3101 — 25 warnings in 6 files:

- `avogadro/io/cjsonformat.cpp` (14)
- `avogadro/io/mdlformat.cpp` (3)
- `avogadro/io/vaspformat.cpp` (3)
- `avogadro/io/xyzformat.cpp` (3)
- `avogadro/io/lammpsformat.cpp` (1)
- `avogadro/io/pdbformat.cpp` (1)

25 warnings in 24 changed lines: `cjsonformat.cpp:1851` carries two of them (`gtoIndices()` and `atomIndices()` in the same condition).

The diff is clang-tidy's own `-fix` output and nothing else: `size() > 0`, `size() != 0`, `size()`/`length()` in a condition and `== ""` all become `empty()`/`!empty()`. 6 files, +24 −24, no hand edits, no other checks, no reformatting.

`mmtfformat.cpp` isn't part of the box: `USE_MMTF` defaults to `OFF` (the top-level CMakeLists marks it "no longer maintained"), and the file is only added to the `IO` target when it is on, so it isn't in the compile database. For the record, it holds one more instance of this check — `mmtfformat.cpp:86`, `structure.spaceGroup.size() > 0` — left out because it's outside the box as counted. Happy to fold it in if you'd rather have the directory clean under `-DUSE_MMTF=ON` as well.

## Commands

Configure and build (headless container, Qt/OpenGL off — `avogadro/io` and its tests don't need them; `avogadrodata` cloned next to the source). The fix was produced with clang-tidy 22; the pre-fix finding set was cross-checked identical under clang-tidy 18:

```
cmake -S . -B build -G Ninja -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DENABLE_TESTING=ON \
  -DAVOGADRO_DATA_ROOT=<avogadrodata> \
  -DUSE_QT=OFF -DUSE_OPENGL=OFF -DUSE_PLOTTER=OFF -DUSE_LIBMSYM=OFF -DUSE_SPGLIB=OFF \
  -DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++ -DCMAKE_BUILD_TYPE=Release
cmake --build build -j3
```

Fix — your command, run from the repository root rather than from `avogadro/`, with the file pattern also matching headers in the same directory (all 25 findings are in `.cpp` files, so that part is inert):

```
run-clang-tidy -p build -checks='-*,readability-container-size-empty' \
  -header-filter='avogadro/io/' -fix 'avogadro/io/.*\.(cpp|h)$'
git clang-format
```

## Verification

- Re-running the same `run-clang-tidy` without `-fix`: **0 warnings** in `avogadro/io`.
- `ctest --test-dir build`: **75/75 passed** (`Io-*` is 16 of them — including `Io-Cjson`, `Io-Mdl`, `Io-Vasp`, `Io-Xyz`, `Io-Lammps` and `Io-Pdb`). Qt/OpenGL were off in that build, so Qt-dependent test targets aren't part of it; CI covers those.
- The full tree still builds after the fix, and `git clang-format` (18 and 22) reports no changes.
- Each substitution is a semantic no-op — `empty()` is exactly the comparison it replaces, so no behavior changes and no API/ABI change (no headers touched).

AI usage: level 0–1, per the contributing guide. The diff is clang-tidy's `-fix` output rather than hand-written code; the workflow and this description were prepared with Claude Code.

Part of #3101.

Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
1 Letterman Drive
Suite D4700
San Francisco, CA, 94129

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.

Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd83a724b7b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.