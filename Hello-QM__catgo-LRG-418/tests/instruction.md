# Issue

**Title:** fix(workflow): teaching templates run e2e + VASP NEB input gen + MLP param-display cleanup

## Description

Makes the frontend teaching/demo workflow templates run end-to-end (local MLP + correct HPC routing) with real per-node results, implements VASP NEB multi-image input generation, and cleans up software-irrelevant param display in the editor. All verified live by driving the actual frontend (Playwright → vite UI → backend), not just API calls.

## Backend — teaching templates run e2e (`3ac5d33`)
Seven real bugs that left templates failing or silently "completed-but-empty":
- **Fan-out**: `loop`/`doping_gen` emit a scalar `structure_json` (first struct) so a single-structure downstream consumer has an input (the "No input structure for MLP step" crash); MLP single consumer falls back to `structures[0]`; the MLP batch bridge re-exposes `structures`+`labels` so `geo_opt → single_point/freq` chains re-fan instead of collapsing to the first structure.
- **Routing**: add `(single_point/freq/cell_opt, mlp)` → `mlp_single_point`/`mlp_vibrations`/`mlp_relax`, register them in `MLP_NODES` (were falling through to the HPC submitter → "No HPC connection").
- **Generic `analysis`**: scanner resolve-gate now includes `analysis`; unmapped/blank analysis kinds route to a new `analysis_passthrough` handler instead of erroring.
- **`free_energy`** moved `LOCAL_NODES` → `ANALYSIS_NODES` (its handler lives in `execute_analysis_node`; it was a no-op COMPLETED before, breaking every recipe's final node).
- **Failure masking**: `execute_local_node` re-raises so the V2 task is marked FAILED (was reporting API errors as "completed").

Verified GREEN on an isolated test backend with MACE: all 6 fan-out templates + band_structure/vasp_double_relax/cp2k_*/full_catalysis/doped_catalyst_screening/adsorption_screening/recipe_NEB, with populated `result_json`. DFT-only nodes (electronic/dos/charge/slow_growth) confirmed submission-ready via dry-run (INCAR/POSCAR/KPOINTS/sbatch generate) — they need HPC, same path ORR uses.

## VASP NEB multi-image input generation (`2aae1ed1`, `5088aa01`)
- Both the local preview (`engine_builtins`) and HPC (`vasp.py`) paths interpolate initial+product into image subdirs `00/POSCAR`..`0(N+1)/POSCAR` + NEB INCAR (IMAGES/IBRION/POTIM/SPRING/LCLIMB). `(ts_search, mlp)` → `mlp_neb` (fixes two pre-existing `test_mlp_neb` assertions).
- NEB **product endpoint** resolves from a second `structure` input when `structure_product` isn't wired (advancer + submitter), mirroring `orca._resolve_neb_product`.
- Verified end-to-end: H diffusion fcc→hcp on Pt(111) (distinct endpoints) → MACE NEB converges with a real **0.94 kcal/mol** activation barrier and proper MEP curve.

## Frontend (`c1b1fef6`, `c9b54c88`, `5430eae4`, `36ae3e03`)
- Render backend `neb` nodes as the TS Search NEB node (migration `neb → ts_search`) — they previously drew edges into an unrendered node.
- Hide software-irrelevant params (kpoints/ENCUT/ISIF/... baked into MLP nodes by `default_params`) from all three readouts: the node-status "Other Parameters", the canvas card preview + "+N more", and the pending-review gate. Display-only; execution already ignored them.

## Verification
Drove the real frontend (vite UI pointed at the test backend): clicked **Run → Local**, watched a workflow go `pending → pending_review → running → completed` with a real MACE energy, and confirmed the NEB result file + filtered param panels render correctly.

Note: the commit list includes a few already-merged (#404–416) commits with different SHAs from squash-merges; the **Files changed** diff is exactly the new work (13 files).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bddb4ef9c6fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.