# Issue

**Title:** fix(workflow): honor locked slab_gen structure instead of regenerating for HPC

## Description

## Symptom (caught on a live HPC run)

The **ORR on Pt(111)** workflow uploaded a **45-atom, no-constraints** POSCAR to Expanse, while the frontend showed a finalized **36-atom** slab with the **bottom 2 layers frozen**. Two wrong things at once:
1. **Atom count** — 45 sent vs 36 shown.
2. **Constraints** — bottom-2-layer freeze (selective dynamics) completely lost; all atoms free.

What the user saw on screen was **not** what ran on the cluster → wasted allocation + physically wrong results.

## Root cause (one cause, both bugs)

`run_slab_gen` (`server/catgo/workflow/builtins_impl.py`) **unconditionally rebuilt** the slab from the bulk + `miller`/`layers`/`vacuum`, ignoring the frontend's lock contract:

> `SlabGenPreview.svelte:58` — *"When locked, preview shows the saved structure_json instead of regenerating"*

The node was locked (`slab_locked: true`) with a finalized `structure_json` (36 atoms, bottom-2-layer `selective_dynamics`). But the backend rebuilt via ferrox → a different layer count (45 vs 36), and since the freeze was stored **on the structure** (not as a `frozen_layers` param), the regenerated slab carried **no** selective dynamics. Any hand-edit in the 3D viewer (atom removal, manual freeze) is lost the same way.

## Fix

When a `slab_gen` node is **locked** and carries a finalized `structure_json`, `run_slab_gen` returns it **verbatim** — preserving atom count and `selective_dynamics` — instead of regenerating. Unlocked nodes still regenerate from params (live-preview semantics, matching the frontend). What the user sees is exactly what is sent to HPC.

```python
if params.get("slab_locked") and params.get("structure_json"):
    sj = params["structure_json"]
    return {"structure": sj if isinstance(sj, str) else json.dumps(sj)}
```

## Verification

- **Real-node end-to-end** (the actual failing workflow's slab_gen params): fixed `run_slab_gen` → **36 atoms**, 4 layers × 9, bottom 2 layers fixed; rendered POSCAR has **18 `F F F` + 18 `T T T`** with a `Selective dynamics` header.
- **Tests** (`test_slab_gen_locked.py`): locked node returns the saved slab verbatim (atom count + SD preserved); unlocked node still regenerates from bulk. **2 passed.**
- TDD: the locked test failed first on current code (regenerated 16 atoms, SD dropped), passes after the fix.
- Pre-existing `TestGibbsEnergy` failures in `test_builtins_execution.py` confirmed failing on base `main` (unrelated).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27f7f553db54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.