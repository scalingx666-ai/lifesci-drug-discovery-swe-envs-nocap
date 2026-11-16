# Issue

**Title:** fix(workflow): wire analysis/export nodes so teaching templates run (no new science code)

## Description

## Context

The frontend workflow editor is for **teaching demos / beginner practice** — real production runs go through the backend + catgo-campaign. But ~13 built-in templates couldn't run at all: they referenced node types that the scanner routed to **"unknown"**, even though the handlers already existed. (A reviewer or a student downloading CatGo would hit dead ends.)

## Root cause — missing wiring, not missing implementations

| Node type | Handler exists in | Was missing from |
|---|---|---|
| `convergence_check`, `energy_compare`, `pick_best`, `her_analysis` | `engines/analysis.py` | `ANALYSIS_NODES` |
| `export_data` | `engines/local.py` | `LOCAL_NODES` |
| generic `analysis` (type=elastic/phonon/…) | the specific `*_analysis` handlers | no `analysis`→specific mapping |
| `elastic_analysis`, `phonon_analysis` | — (frontend renders the plots) | hit the else-branch `RuntimeError` |

## Fix (no new science code)

- Add the post-processing node types to `ANALYSIS_NODES` / `LOCAL_NODES`.
- `_resolve_software` maps a generic `analysis` node to its existing type-specific handler via `params["type"]`.
- `execute_analysis_node` gains lightweight collect-and-pass-through handlers for `elastic_analysis`/`phonon_analysis` (the elastic-tensor / phonon visualization is rendered frontend-side for the demo; production-grade analysis is catgo-campaign's job) — so the node completes instead of raising.

## Result

Of the originally-flagged unrunnable templates, all now route to a real handler **except** `neb` (genuinely needs a NEB engine) and the degenerate `analysis type=re-optimize` retry branch in `adsorption_screening`.

## Test

`test_analysis_node_wiring.py` — routing + `analysis`-type resolution + elastic/phonon handlers present. **4 passed.**

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `418e698523c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.