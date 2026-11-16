# Issue

**Title:** fix(workflow): adsorbate-only freeze for freq in catalysis recipes + templates (C2)

## Description

## What

A deterministic physics audit of all **32 built-in templates + quickbuild recipes** (all pass mechanical dry-run) flagged **6** with the same methodology bug — and 26 clean.

The 6: `HER`, `OER`, `ORR`, `NRR`, `CO2RR_2e` recipes + the `Full Catalysis Pipeline` template. Their **freq** nodes on adsorbate/slab systems used `freeze_mode=bottom` (or none) instead of `adsorbate`, so the top slab layers vibrate → wrong ZPE/entropy in the free-energy diagram.

## Fix

- **Quickbuild `vasp_freq` preset** (`server_claude_code.py`): `freeze_mode: bottom` → `adsorbate`. Fixes all 5 catalysis recipes at once. `vasp_opt` keeps bottom-N (correct for geo_opt).
- **Full Catalysis Pipeline** (`graph-model.ts`): adsorbate `geo_opt` gains `frozen_layers: 2`; `freq` gains `freeze_mode: adsorbate`.

Builds on `freeze_mode=adsorbate` (#407).

## Test

`test_recipe_freq_freeze.py` — every adsorbate recipe's freq node uses `adsorbate`; geo_opt keeps bottom-layer freeze. **Passes.**

## Audit coverage

26/32 templates clean (bulk/molecular ones correctly have no freeze; freq-bearing adsorbate ones now all `adsorbate`). 0 broken. Audit was rule-based (slab-geo_opt-no-freeze / adsorbate-freq-not-adsorbate / ENCUT-IBRION-ISIF sanity).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `418e698523c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.