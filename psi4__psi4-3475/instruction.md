# Issue

**Title:** Gate DFT method registration on runtime LibXC availability

## Description

## Description

`import psi4` instantiates every functional in the DFT dictionary at import time (`proc_table`). If a definition references a LibXC method that is **absent from the linked LibXC build** — most commonly a functional **renamed between LibXC versions** — the C++ `LibXCFunctional` constructor aborts and the whole `import psi4` fails. The registry never checked whether a functional was actually provided by the runtime library before advertising it as an available method.

The concrete trigger (issue #3474): `GGA_XC_TH_FL` was reclassified to `LDA_XC_TH_FL` in LibXC 7.1, so importing Psi4 against LibXC ≥ 7.1 died with *"Could not find required LibXC functional XC_GGA_XC_TH_FL"*.

This fixes the underlying cause — no runtime availability check — rather than chasing individual renames.

## What changed

**C++ — a runtime availability primitive**
- `LibXCFunctional::available(name)`: a static, allocation-free lookup (`xc_functional_get_number(name) != -1`; it does **not** build the functional), exposed to Python as `core.LibXCFunctional.available`.

**Python — gate the builds on availability**
- `dft_builder.libxc_functionals_in_dictionary(func)` enumerates the LibXC methods a definition depends on: the `xc_functionals` special case, the `x_functionals`/`c_functionals` components, and a GGA borrowed for exact exchange via `x_hf`/`use_libxc` — exactly the names `build_superfunctional_from_dictionary` hands to LibXC.
- `dft_builder.functional_available(func)` checks them all against the runtime library.
- `build_superfunctional_from_dictionary` now raises a clear `ValidationError` naming the missing method(s) instead of aborting mid-build.
- `proc_table` skips functionals whose LibXC dependencies are absent, rather than crashing the import — they are simply not registered as available methods.

**TH-FL works on any LibXC version**
- With detection in place, the TH-FL definition lists **both** spellings (`LDA_XC_TH_FL`, `GGA_XC_TH_FL`) and registers whichever the linked LibXC provides — no version branching. On LibXC ≥ 7.1 it resolves to `LDA_XC_TH_FL`; on < 7.1 to `GGA_XC_TH_FL`.

## Validation

New `tests/pytests/test_libxc_availability.py` (7 cases, all pass): the availability check (true/false), dependency extraction, the `functional_available` gate, the clear-error build path, and TH-FL dual-spelling registration; plus a no-over-pruning sanity energy.

Manually verified against **system LibXC 7.1.2**: `import psi4` now succeeds **unpatched**, TH-FL is registered via `LDA_XC_TH_FL`, and all 1619 DFT/SCF energy methods register (none over-pruned).

## User API & Changelog
- [x] `import psi4` no longer aborts when a dictionary functional is missing from the linked LibXC (e.g. renamed between versions); such functionals are skipped, and an explicit request yields a clear error naming the missing method.
- [x] TH-FL works on LibXC both `< 7.1` (`GGA_XC_TH_FL`) and `>= 7.1` (`LDA_XC_TH_FL`).
- [x] new `core.LibXCFunctional.available(xc_name)` helper.

## Checklist
- [x] Tests added for the new behavior
- [ ] Docstring/narrative docs — n/a (internal registry behavior)

## AI
- [x] AI usage: implementation and finite-scope validation (import/registration checks against LibXC 7.1.2).

## Status
- [x] Ready for review

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a26085888838`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.