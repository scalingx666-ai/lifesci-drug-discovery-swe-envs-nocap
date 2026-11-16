# Issue

**Title:** fix(slab): orthogonalize c by default so the surface plane is ab

## Description

## Problem
The interactive / MCP slab tool (`POST /structure-ops/generate-slab`, used by `catgo_structure action="slab"` and the CLI) defaulted `orthogonalize_c=False`. pymatgen's `SlabGenerator` then returns the **oriented** cell, whose **c-vector is tilted** (not perpendicular to the ab surface plane) for non-orthogonal cuts (e.g. FCC(111)). That slab is unusable for surface DFT — vacuum is not cleanly along c.

This only affected the **pymatgen** path. The frontend WASM cutter and the ferrox primary path already produce c⊥ab.

## Fix
- `GenerateSlabRequest.orthogonalize_c` now defaults to **True** (`structure_ops.py`) → `get_orthogonal_c_slab()` runs by default. `orthogonalize_c=False` still available to keep pymatgen's oriented cell.
- The workflow `slab_gen` **pymatgen fallback** (`builtins_impl.py`) now also orthogonalizes c, matching the ferrox primary path.

## Test / verification
- New `server/tests/test_slab_orthogonalize.py` (2/2): default FCC(111) slab has c⊥ab; the flag still works when explicitly disabled.
- Live: `curl POST /api/structure-ops/generate-slab` FCC(111) → `cos(c,a)=cos(c,b)≈1.6e-16` (c⊥ab).
- Regression: isolated run of the broader slab/structure/workflow set matches pristine `main` (the 6 failing there are pre-existing — `test_claude_code_mcp` registry drift, `test_expanse_e2e`, `test_workflow_engine*` — and `test_lateral_hetero_mcp` is import-order flaky, all unrelated to this change).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `733aecb853f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.