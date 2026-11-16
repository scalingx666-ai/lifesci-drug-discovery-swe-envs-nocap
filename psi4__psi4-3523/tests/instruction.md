# Issue

**Title:** Remove dead libmints/fjt Boys-function module

## Description

The hand-rolled Boys-function classes in `libmints/fjt.{cc,h}` — `Fjt`, `Taylor_Fjt`, `FJT`, `GaussianFundamental` and the F12/Erf fundamentals — are dead. Boys/ERI evaluation goes through libint2, and nothing in the tree references any of them; the files were still compiled and `#include`d by `eri.cc`/`eribase.cc` but unused.

This removes:
- `fjt.cc` / `fjt.h` (~1030 lines) and the CMake source entry
- the now-unused `#include "psi4/libmints/fjt.h"` from `eri.cc` and `eribase.cc`
- the stray `class Fjt;` forward declaration in `eri.h`

No functional change. `CorrelationFactor` (forward-declared in `fjt.h`) is still provided to `eri.cc`/`eribase.cc` via `integral.h`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd6027de91f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.